# Mapowanie diagramu klas UML na relacyjną bazę danych

Diagram klas został przekształcony w model relacyjnej bazy danych zgodnie z zasadami mapowania UML na relacyjny model danych.

Każda klasa UML została odwzorowana jako tabela w bazie danych:
- Klasa `Klient` → tabela `Klienci`
- Klasa `Sprzedawca` → tabela `Sprzedawcy`
- Klasa `Samochod` → tabela `Samochody`
- Klasa `Zamowienie` → tabela `Zamowienia`
- Klasa `Producent` → tabela `Producenci`

Atrybuty klas zostały odwzorowane jako kolumny tabel, natomiast relacje pomiędzy klasami zostały zrealizowane za pomocą kluczy głównych (PK) oraz kluczy obcych (FK).

Relacje typu:
- 1:N zostały odwzorowane poprzez dodanie klucza obcego do tabeli podrzędnej,
- relacje pomiędzy zamówieniami a klientami, sprzedawcami i samochodami zostały zrealizowane przy pomocy kluczy obcych w tabeli `Zamowienia`.

Zastosowano integralność referencyjną oraz reguły `CASCADE` i `SET NULL` dla wybranych relacji.

---

# Normalizacja relacyjnej bazy danych

Projekt relacyjnej bazy danych został znormalizowany do trzeciej postaci normalnej (3PN).

## Pierwsza postać normalna (1PN)

Każda tabela posiada klucz główny, a wszystkie wartości atrybutów są atomowe i niepodzielne.

Przykłady:
- `idKlienta`
- `idSprzedawcy`
- `VIN`

W tabelach nie występują grupy powtarzające się.

---

## Druga postać normalna (2PN)

Wszystkie atrybuty niekluczowe są zależne od całego klucza głównego.

Przykład:
- dane klienta zależą od `idKlienta`,
- dane samochodu zależą od `VIN`.

Nie występują zależności częściowe.

---

## Trzecia postać normalna (3PN)

Usunięto zależności przechodnie pomiędzy atrybutami niekluczowymi.

Dane producentów, klientów oraz sprzedawców zostały wydzielone do osobnych tabel:
- `Producenci`
- `Klienci`
- `Sprzedawcy`

Dzięki temu ograniczono redundancję danych oraz możliwość występowania:
- anomalii aktualizacji,
- anomalii usuwania,
- anomalii dodawania danych.

Znormalizowana struktura bazy danych zwiększa spójność oraz integralność danych systemu.
