---
title: "instal·lar ubuntu"
date: 2008-01-07
forum: Catalan Team
---

### Post by bratac on 2008-01-07
Bones,

vull instal·lar ubuntu en un ordinador nou amb 160 gO. El que em plantejo és si partir el disc o no. Vull dir, si parteixo el disc i en faig una partició (20gO) per a l'ubuntu una altra per la swap (5gO) i la resta 135 gO com a espai per a emmagatzemar els treballs, vídeos, cançons... o no partir el disc. Vull saber si  hi ha alguna manera de vincular la carpeta *home* a l'altra partició o senzillament faig una instal·lació normal i passo de la carpeta home.

Si vull fer particions és per poder fer les actualitzacions sense haver de patir massa per a les dades desades.

No sé si m'he sabut explicar molt bé, però agrairia opinions.

fins ara,

---

### Post by papapep on 2008-01-07
> vull instal·lar ubuntu en un ordinador nou amb 160 gO. El que em plantejo és si partir el disc o no. 

T'aconsello particionar el disc. Sempre ajuda en cas de reinstal·lacions.

> Vull dir, si parteixo el disc i en faig una partició (20gO) per a l'ubuntu una altra per la swap (5gO) i la resta 135 gO com a espai per a emmagatzemar els treballs, vídeos, cançons... o no partir el disc.


(Per cert, es diu Gb, no gO) Doncs amb 20 gigues de sistema crec que en tindràs suficient, excepte que t'instal·lis tot el que et passi per les mans. La swap amb 2 Gb vas sobrat, més no serveix per a gaire.(també depèn de la RAM física que tingui el sistema) i la resta doncs per les teves coses i que quan vulguis, hagis, o el que sigui, de tocar el sistema operatiu no ho perdis tot.

> Vull saber si hi ha alguna manera de vincular la carpeta home a l'altra partició o senzillament faig una instal·lació normal i passo de la carpeta home.


No acabo d'entendre la teva pregunta. Suposo que deus tenir un error de concepte. Quan tu montes la partició /home a Linux li és igual que la tinguis en una sola partició, en una altra diferent del sistema o en  un altre disc, local o remot. La munta i per a tu segueix essent la teva /home. Era això el que preguntaves??

---

### Post by Joan Marc on 2008-01-07
> Vull saber si hi ha alguna manera de vincular la carpeta home a l'altra partició o senzillament faig una instal·lació normal i passo de la carpeta home. 

El que vol dir en papapep, és que /home, forma part del sistema (és com dir-ho d'una manera, els Documents and Setings del Windows), i per tant, per si sol, s'instal·la a la mateixa partició de la resta de l'ubuntu que és la /(root).
 El que volies dir tu, en part, és si era recomanable fer una partició de nom /home, i que tot els teus documents, fotos, vídeos [etc], es guardessin en una partició diferent de la resta de l'ubuntu que és la /(root).
Tal i com em va dir en papapep, si que és millor crear una partició amb nom /home, i així tenir-ho tot més segur.

Espero no m'hagi liat gaire ;)
Salut!

---

### Post by eselma on 2008-01-08
> **papapep said:**
> 
(Per cert, es diu Gb, no gO)....

D'acord amb tot el que diu en Papapep (per descomptat!)... menys en això. 
Go (i no gO, efectivament) és una notació que va a començar a córrer els anys 70 i 80, manllevada del francès, que encara la fan servir (Go => Giga octet). En català, i dins de l'àmbit matemàtic, un octet és un conjunt de vuit objectes que tenen una propietat comuna.

Posteriorment l'IEC va normalitzar els mots bit i byte:

[I][COLOR="DarkGreen"]bit: Unitat mínima de mesura del contingut informatiu d'un missatge transmès per un sistema informàtic o un sistema de telecomunicacions, equivalent a triar una possibilitat del sistema entre dues, 0 o 1. Nota: Bit és un acrònim de l'anglès binary digit. No se sol abreujar quan s'usa aïlladament; quan intervé en la formació d'altres abreviacions, tant s'usa bit com b. 

Byte: Cadena de bits de longitud fixa, habitualment 6 o 8, tractada com a unitat per un ordinador i que generalment correspon a un caràcter del codi ASCII. Nota: En un sentit estricte octet designa la cadena formada per 8 bits, mentre que byte denomina qualsevol cadena de bits; ambdues denominacions es consideren, però, sinònimes atès que actualment un byte generalment està constituït per 8 bits. Byte és un acrònim de l'anglès binary term. Se sol abreujar internacionalment amb la forma B[/COLOR][/I]

(Definicions del TERMCAT).

Per tant, atès que tots els múltiples cal representar-los en el Sistema Internacional per una majúscula (llevat del kilo), caldria representar mili milions de bits amb el símbol Gb, i mil milions de Bytes amb GB (les dues majúscules. Aquestes són les unitats que usen normalment els fabricants de discos durs.

Una altra cosa és considerar 2 elevat a 30 (1073 MB, aproximadament). Això fora un GiB, una quantitat pràctica en maquinari, però diferent.

Perdoneu l'*off-topic*.

---

### Post by papapep on 2008-01-08
Buffff...val, cap problema, accepto la classe. Per cert, seria possible que m'escrivissis bé el malnom?? :-)

---

