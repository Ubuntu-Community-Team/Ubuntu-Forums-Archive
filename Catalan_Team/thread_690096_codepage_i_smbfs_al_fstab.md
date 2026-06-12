---
title: "codepage i smbfs al fstab"
date: 2008-02-07
forum: Catalan Team
---

### Post by guillemsola on 2008-02-07
Hola a tothom!

Tinc un disc dur en xarxa (NAS) que munto de la següent manera:

> sudo mount -t smbfs //192.168.1.3/PUBLIC /mnt/NAS/ -o guest,iocharset=utf8,dmask=777,fmask=777,codepage=iso8859-15,uid=1000

fent això els accents i caràcters especials els visualitzo perfectament.

total que al portàtil perquè es connecti en quant entri la wifi vull fer això des de fstab amb l'opció user:

> //192.168.1.3/PUBLIC    /mnt/NAS        smbfs   user,guest,iocharset=utf8,codepage=iso8859-15,uid=1000 0       0

D'aquesta manera el munto peo no carrega bé el codepage i no mostra correctament els caràcters especials. (si amb l'ordre mount)

Alguna idea? Fins el que jo se aquestes dues ordres haurien de tenir el mateix comportament.

gràcies

---

### Post by CarlesOriol on 2008-02-07
Jo faig uid=1000,gid=1000,codepage=cp850,iocharset=utf8

---

### Post by guillemsola on 2008-02-07
Amb els codepages d'aquest trasto fa un any que m'hi barallo. L'aparell és un disc dur en xarxa autònom conceptronic o sigui que ja us podeu imaginar... De totes formes té un menú on es pot codificar a cp1252 que és el codepage per western europe. Si el munto amb el cp1252 alguns caràcters no lo agraden i amb el cp850 tampoc.

El tema està en que si munto amb sudo mount .... no tinc cap problema per accedir al dispositiu, però si faig una línia a fstab per muntar-lo aleshores sembla que "passi" dels codepage que li poso.

Per això preguntava si hi passa alguna cosa amb els codepages de samba a fstab.

salut!

---

### Post by CarlesOriol on 2008-02-07
i al fstab així... noauto,user,quiet,showexec,iocharset=utf8,codepage=850 et funciona?

---

### Post by guillemsola on 2008-02-08
uhmm, he provat el que m'has proposat i amb l'opció noauto no em munta el disc.

De totes formes en principi no tinc problemes per muntar el disc en xarxa des de fstab sinò que el problema el tinc en que passa de mi respecte al codepage.

En principi faig servir l'opció iocharset=utf8 (que es correspon al meu locale) i codepage=iso8859-1 (del disc en xarxa) per fer la conversió.

El problema radica en que tan si poso les opcions anteriors o unes altres ( les he provat totes ) no em fa la conversió de caràcters i els accents no es veuen correctament.

En canvi si munto amb les mateixes opcions de locales i codepage amb l'ordre mount fa la conversió perfectament.

Ho he provat en 2 ubuntus, 1 debian i 1 gentoo i a tot arreu el comportament és el mateix. No se si és que com que aquestes coses les inventen els güiris i ells no fan servir accents... potser és perquè pel que he llegit l'opció smbfs està obsoleta i recomanen fer servir cifs que el meu servidor NAS no suporta.

gràcies

---

### Post by CarlesOriol on 2008-02-08
No, no ... sols volia dir la part de: codepage=cp850,iocharset=utf8

Jo vaig tenir el mateix problema fa temps... però aquests dies estic fora de casa i no et pu enviar el meu fstab... 

Si no et va el que t'he dit demà postejo el que funciona segur ;-)

Ah... i si és smbfs o cifs  crec que no té res a veure.

---

### Post by guillemsola on 2008-02-08
Doncs ja m'ensenyara el teu fstab pq a mi no em tira XD

De moment estic muntant des del crontab de root amb

> @reboot mount -t smbfs //192.168.1.3/PUBLIC /mnt/NAS/ -o guest,iocharset=utf8,dmask=777,fmask=777,codepage= iso8859-15,uid=1000

i això si que li agrada!

---

### Post by CarlesOriol on 2008-02-14
Ostres...

No m'havia fixat que la màquina on ho tenia (crec que ho vaig configurar a la dapper) ja no va bé.

Fins i tot els noms llargs dels arxius en smbfs no estan bé amb la mateixa configuració de fstab que abans anava.

Ho sento... sembla que estic igual d'enganxat que tu :-)

---

### Post by guillemsola on 2008-02-14
Quines coses que té la informàtica!

Desprès de barallar-mi força ho he resolt muntant les particions a l'arrencada al crontab a 2 màquines que van per cable..

Sorprenentment al portàtil que no té xarxa fins que no connecta per wifi si que em funcionen a fstab! Crec que hauria de ser més fàcil amb cable però suposo que ara ja nomes "optimitzen" per que funcioni amb wifi??

Munto dues particions samba i una pot anar indistintament amb cifs o smbfs. Aquesta darrera s'assembla més a un finestres i la faig amb el cp=850.

> Lo important és que al codepage has d'assignar el codi de caràcters que hi ha al recurs remot i al iocharset el que tens a la màquina local.

Potser que el que et passi és que com que fa temps que ho vas instal·lar, algun dels 2 sistemes hagi canviat de codi de caràcters. Per comprovar al sistema linux has de fer un locale i comprovar si fas servir ut8 o l'antic iso8859-15.

Salut!

---

