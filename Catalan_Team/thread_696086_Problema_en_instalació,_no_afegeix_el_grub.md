---
title: "Problema en instalació, no afegeix el grub"
date: 2008-02-13
forum: Catalan Team
---

### Post by lluisalguero on 2008-02-13
Hola nois,
avui li he estat instal·lant a un veí l'Ubuntu (li vaig ensenyar el meu i vol provar-lo) i "tenim" un problema, a veure si m'explico bé.

L'imatege ISO l'hem baixada d'aquí -> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) i la versió és la estàndard.

En ficat en marxa el pc desde el cd i ens ha carregat el Live CD, hem instalat i gairebé al final, ens ha sortit un missatge que no s'havia instalat el grub. Reiniciem el pc (ara sense el cd) i efectivament, no surt el menú per triar el sistema operatiu. Tornem a arrencara desde el LiveCD i comprovo i si, s'ha creat la partició i estàn totes les carpetes i arxius.

La configuració dels discos durs es:

Disc 1: 2 particions (WXP i dades)
Disc 2: 3 particions (dades, ubuntu i swap)

La meva incògnita és si em fet malament d'instal·lar l'Ubuntu a un disc físic diferent on està el WXP o bé al moment d'instal·lar se'ns ha passat per alt alguna cosa al moment de configurar les particions.

Ens tocarà fer una instal·lació nova o editant alguna cosa ja podrem arreglar-ho?

Gràcies pel vostre ajut

---

### Post by papapep on 2008-02-13
> La meva incògnita és si em fet malament d'instal·lar l'Ubuntu a un disc físic diferent on està el WXP

Actualment ja no ha d'haver problema amb això.

> o bé al moment d'instal·lar se'ns ha passat per alt alguna cosa al moment de configurar les particions.

Això es impossible que ho sapiguem nosaltres. No hi erem mentres ho feieu :-D

Jo el que faria, és engegar l'ordinador amb un cd amb l'alternate i un cop en el procés de instal·lació anar a la opció de crear el grub i intentar crear-lo així.

---

### Post by lluisalguero on 2008-02-13
> **papapep said:**
> Actualment ja no ha d'haver problema amb això.



Això es impossible que ho sapiguem nosaltres. No hi erem mentres ho feieu :-D

Jo el que faria, és engegar l'ordinador amb un cd amb l'alternate i un cop en el procés de instal·lació anar a la opció de crear el grub i intentar crear-lo així.

Gràcies papapep...miraré de fer això que em dius

---

### Post by CarlesOriol on 2008-02-14
Doncs jo no faria això.

Primer miraria per que no se us ha insta&#320;lat el grub. Una possibilitat és que la placa mare tingui activada algun tipus de protecció antivirus que bloquegi l'accés als sectors d'inici. Comrpoveu-ho per què si no serà perdre el temps.

Despres iniciaria amb el disc normal i restauraria el grub fent

sudo grub

root (hdo0,0)
setup (hd0)
quit

i reiniciaria.

Tot i que si no sempre podeu provar la versió de l'instalador en mode text... sort que no n'hi ha amb tarjetes perforades sinò en papapep ens faria anar a tots a la llibreria a comprar cartolines :-D

---

### Post by SiscoGarcia on 2008-02-14
```
... sort que no n'hi ha amb tarjetes perforades sinò en papapep ens faria anar a tots a la llibreria a comprar cartolines

```=D>

EXCEL·LENT, Carles. (No he pogut evitar d'apuntar-ho, he rigut una bona estona)

---

### Post by papapep on 2008-02-14
Sou una colla de, de, de....ara no em surten les paraules.... :-P

---

### Post by eselma on 2008-02-14
> **SiscoGarcia said:**
> ```
... sort que no n'hi ha amb tarjetes perforades sinò en papapep ens faria anar a tots a la llibreria a comprar cartolines

```=D>
EXCEL·LENT, Carles. (No he pogut evitar d'apuntar-ho, he rigut una bona estona)

Que teniu en contra de les targes perforades? És una manera prou bona de depurar el codi "visualment". A més, les *IBM* de 80 columnes són més compactes que les clàssiques *Hollerith* de 72!

Això si, són més voluminoses que les cintes (les perforades *ANSI* de paper), però no s'embussen amb el cel·lo com aquestes. :)

---

### Post by papapep on 2008-02-14
Us recomano a tots plegats que mireu una sèrie de tv que es diu [Life on Mars]("http://www.bbc.co.uk/lifeonmars/"), de la BBC, on els més jovenívols (Carles, sàpigues que NO hi quedes inclós) podreu experimentar el trauma del retorn a la era "pre-electrònica de consum massiu" :-D (a banda, la trobo una sèrie excel·lent).

---

### Post by SiscoGarcia on 2008-02-14
> Que teniu en contra de les targes perforades?

No és contra les targes perforades ni contra ningú ni res. L'acudit podria haver estat el mateix parlant de la "tabula rassa" enlloc de les targes perforades. ;)

---

### Post by Miquel Ubuntero on 2008-02-14
Hola Papapep i altres.
Tornant al tema del alternate CD. He estat intentant cercar com carregar el GRUB a un disquette però no ho he vist. Si recordes, fa uns dies, en un altre post vaig comentar la necesitat de iniciar el GRUB amb disquetera i encara no ho he aconseguit.
Sabeu d'algun tutorial x novatos? Tutorial del alternate i el GRUB.

O be, millor encara, algú coneix algún programa rollo "Boot Manager"?

Air vaig  grabar com si fos imatge a un diskete, el sbm.bin que vaig trobat en un Ubuntu CD, però no va gaire fi. No em xuta si l'indico de botejar des de USB.

Cap idea?

P.D.: Espero haberme expresat prou be, tenint en comte que no soc informàtic.
Salut!

---

### Post by guillemsola on 2008-02-15
Per posar el grub en un disquet jo ho faig així:

primer crees una carpeta per muntar el disquet, per exemple

  # mkdir /mnt/floppy

després el formatejes, per exemple amb ext2

   # mke2fs /dev/fd0

després el muntes

   # mount -t ext2 /dev/fd0 /mnt/floppy

instal·les grub

   # grub-install --root-directory=/mnt/floppy fd0

copia el menu.lst del teu sistema al disquet

  # cp /boot/grub/menu.lst /mnt/floppy/boot/grub/menu.lst

finalment el desmuntes.

   # umount /mnt

si vols suposo que pots formatejar el disquet des de el nautilus i tb copiar el menu.lst

Salut!

---

