---
title: "Muntar el DVD extern"
date: 2008-03-22
forum: Catalan Team
---

### Post by almogabber on 2008-03-22
Bones!

Fa uns dies vaig preguntar, i em vau resoldre, com muntar un pendrive. Més que entendre-ho, vaig fer simplement el que em dèieu alguns i va funcionar. Perfecte. Però la [solució donada en aquell cas]("http://ubuntuforums.org/showpost.php?p=4357845&postcount=8") no em serveix ara.

Ara em passa el mateix amb un lector de dvd extern. Fins ara funcionava perfectament. Sense haber de muntar res; a la primera de forma automàtica. Ara res de res. Bé, el localitza i el reconeix (apareix amb els altres lectors i hd's que tinc) però a l'hora de llegir el dvd o cd diu que:> 
No es pot muntar el medi. És possible que no hi hagi cap medi a la unitat

El que no sé és si s'ha trencat el lector per alguna cosa, ja que no el sento ni girar tot revolucionat per trobar quelcom. I a més, amb windows passa 3/4 del mateix.
Però si no s'ha mogut d'aquí la taula, no es pot trencar així com així.

Em podrieu dir què us sembla que pot passar? o com muntar-lo.

Gràcies!!!

---

### Post by crazyserver on 2008-03-22
Jo voto per queè s'ha trencat XD.
desconecta'l, conecta'l i just després fes:
```
 dmesg | tail
```
Potser trobes alguna pista...;)

---

### Post by papapep on 2008-03-22
> Però si no s'ha mogut d'aquí la taula, no es pot trencar així com així.

Ah no??? I tant que pot!! Tu has vist algun xip o component electrònic moure's abans de "morir-se"?? :-D

Si té alimentador extern, assegurat de que arriba tensió, i que sigui la correcta, a la unitat de DVD (un multímetre, aka "tèster", farà la feina).
Evidentment, donem per entès que has verificat que el cable DVD<->PC funciona correctament, etc.

---

### Post by almogabber on 2008-03-22
Si si, funcionar funciona (o si més no en gran part). des de l'aparell en si (obrir i tancar-lo) com des de l'explorador, perdó: nautilus, on sense cap problema també obre i tanca sense més (botó dret: expulsar).
la sortida de un dmesg | tail és el següent (jo no sé veure-hi res):
> [   71.999940] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   72.347281] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   72.387518] NFSD: starting 90-second grace period
[   74.844765] Capability LSM initialized
[21401.307841] usb 1-2: USB disconnect, address 2
[21411.006561] usb 1-2: new full speed USB device using uhci_hcd and address 3
[21411.170566] usb 1-2: configuration #1 chosen from 1 choice
[21411.173684] scsi1 : SCSI emulation for USB Mass Storage devices
[21411.173956] usb-storage: device found at 3
[21411.173961] usb-storage: waiting for device to settle before scanning


Sobre de que no s'ha mogut, em referia a que jo (ni ningu, que jo sapiga) l'ha mogut. He vist xips agonitzant, xo no, per ells mateixos no es movien :lolflag:

I el cable, hauria de funcionar, sinò ja no apareixeria ni a la llista de medis que tinc a l'ordinador, oi?

merci!! (per fi plou una mica!!!!)

---

### Post by CarlesOriol on 2008-03-23
> **papapep said:**
> Ah no??? I tant que pot!! Tu has vist algun xip o component electrònic moure's abans de "morir-se"?? :-D.

Tu no has vist blade runner oi?

---

### Post by papapep on 2008-03-23
> Tu no has vist blade runner oi? 

Només m'enrecordo de la [Sean Young]("http://www.philipkdick.com/images_photos-xxxyyy/bladerunner-young-01-.jpg"). :twisted:

---

### Post by crazyserver on 2008-03-23
Bé...bé...
Dedueixo que el CD l'endolles al PC per usb. Almenys així ho diu el dmesg i així és com te l'ha detectat.
El que trobo a faltar és:
usbcore: registered new interface driver usb-storage, o semblant darrere del usb-storage: waiting for device to settle before scanning...
Potser no acabi de funcionar bé...
D'altra banda dius que pel nautilus el pots obrir i tancar... I no el pots muntar?
Si des del nautilus no pots, prova:
```
cat /proc/partitions
```
On hauria de surtir-te una llista de les particions muntables del sistema, trobaras un sdaX o hdaX on X son molts números, per exemple, en el meu cas:
```
major minor  #blocks  name

   8     0  195360984 sda
   8     1   30716248 sda1
   8     2   15358140 sda2
   8     3    2048287 sda3
   8     4  147235725 sda4
   8    16    1023872 sdb
   8    17    1022960 sdb1
```
sdaX els descarto pq són molts i el cd no té particions i m'hi fixo en sdb1 que suposo que serà el cd (en el meu cas es un usb) i faig.
```
sudo mount /dev/sdb1 /media/cdrom
```
Això muntarà el dispositiu /dev/sdb1 al directori /media/cdrom.
En cas de dirte que el directori no existeix crea'l primer:
```
sudo mkdir /media/cdrom
```
o fes servir un altre directori (que estigui buit!)

Potser et trobes que no hi ha número simplement hi ha sdb i prou, en aquest cas fes-ho sense número.
També pot ser que sigui hdb1, pèro sent un dispositiu USB no ho crec.

Bé a mi se m'acaben les solucions, però si windows tp el reconeix, ves fent un foradet en una jardinera per enterrar-lo.

---

