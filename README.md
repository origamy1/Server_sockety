# Server_sockety

Tento server momentálne nerobí v podstate nič len príjme data od servera na určitom porte.  Momentálne je to tak spravené že mu chodia dáta v takomto formáte.
1|12|message+/0   toto bude odosielaný formát serveru  pričom končí lomenou nulou     pričom prvé číslo hovorí od koho prišla správa, druhé čislo komu má prísť správa.
potom pride správa. a /0 ako ukončenie reťazca. je to vždy navyše bajt. Pre lepšiu pracu so stringom na strane servera. dá sa teraz využiť strlen() pre určenie veľkosti reťazca.

no 
 Teraz treba implementovať, Že server si uloží prijatú správu do súboru. appendne ju na koniec texťáku.
                takto bude appendovať od každého klienta. 

                Treba zariadiť, aby sa na server mohlo pripojiť viacero klientov
                a všetky prijaté správy od všetkych klientov bude ukladať do toho istého súboru. (multiThreads?)

                Vždy keď sa aktualizuje súbor, tak aktualizuje vybraným dvom chatom ich správy, teda prehľadá textový súbor
                a odošle nim určené správy nazad dvom klientom, ktorych sa týkala posledná správa.

                Následne, keď tieto správy príjme klient, tak ich spracuje do poľa správ.
                Teraz treba vymyslieť metódu, ktorá toto pole správ vykreslí v rect pre chat

                Čo možno upraviť, to je spraviť objekt plocha, kde budú objekty ako RECT pohromade.
                
                
                

Su dve možnosti ako to spraviť
                
1. Synchronne. Pravdepodobne komplikovanejšia možnosť. ale vhodné pre neobmedzený počet klientov. keby teoreticky túto aplikáciu používalo
miliarda zariadení.  Šlo by to. len trebalo by riešiť veľa synchronizačných problémov
2. Asynchrónne. Tu je nápad taký, že pre každý soket bude bežať osobitné vlákno. a toto vlákno bude cez mutex ukladať dáta buď do databázy,
alebo v tomto prípade do súboru. vždy sa locknú ostatné vlákna od prístupu k databáze. Uloží sa do súboru správa ktorá prišla od niektorého z klientov.

