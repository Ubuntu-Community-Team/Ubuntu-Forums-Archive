---
title: "[SOLVED] posar /home a partició per a dades"
date: 2008-12-01
forum: Catalan Team
---

### Post by jinglada on 2008-12-01
Com es posa /home a la nova partició i com es canvien les definicions a /etc/fstab per a que el nucli sàpiga on hi ha el nou /home a l'hora d'arrencar?

---

### Post by open-pitu on 2008-12-01
Bones! No em queda massa clar tot plegat i per tant et respondré al que em sembla entendre, sinó no anem pel mateix camí dóna més informació.

Mira, una solució ràpida (i no per això dolenta) seria crear-te un softlink. Amb això podries crear una carpeta en el teu home, on el seu contingut es guardés a la partició de dades. La comanda seria semblant això:
```
ln -s PATH_ORIGEN PATH_DESTÍ
```
Exemple per a apache:
```
ln -s /var/www /home/pitu/www
```
Exemple per a partició de dades:
```
ln -s /media/dades /home/pitu/dades
```

En el cas que el que vulguis fer sigui montar per defecte la teva partició de dades en algun punt has de modificar el fitxer fstab.
```
sudo gedit /etc/fstab
```
I busques la línia que carrega la teva partició de dades, en el meu cas és així:
```
# /dev/sda2
```
```
UUID=8131-7FD2  /media/dades    vfat    defaults,umask=007,gid=46 0       1
```

Doncs hauries de canviar la ruta /media/dades.

Si no era per aquí ja ho diràs.

---

### Post by jinglada on 2008-12-02
Hola open-pitu, gràcies per respondre.

Això ve del que em va dir papapep al fil [http://ubuntuforums.org/showthread.php?t=992972&page=2](http://ubuntuforums.org/showthread.php?t=992972&page=2)
"Un cop fet això [la partició], hauràs de copiar, per exemple, el /home a la nova partició i canviar les definicions a /etc/fstab per a que el nucli sàpiga on tens el nou /home a l'hora d'arrencar."

Jo vaig moure totes les meves dades a la nova partició i ara el meu /etc/fstab té això:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=7c97fe75-576a-4e19-a86e-06f45a077fb2	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=208e6e73-641d-43f6-af8b-4b4495f62a58	/media/disk	ext3	defaults,nosuid,nodev,uhelper=hal	0	2
#Entry for /dev/sda5 :
UUID=5de44525-5115-4e83-8af3-9af0102ab58b	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

Llavors m'interessaria que em diguéssiu què és el més recomanable i/o pràctic en cas, per exemple, de que hagi de formatar la partició on hi ha el sistema operatiu: fer un soft-link o  muntar la partició de dades de tal manera que el nucli sàpiga on tinc el nou /home a l'hora d'arrencar, com diu papapep?

---

### Post by papapep on 2008-12-02
> Llavors m'interessaria que em diguéssiu què és el més recomanable i/o pràctic en cas, per exemple, de que hagi de formatar la partició on hi ha el sistema operatiu: fer un soft-link o muntar la partició de dades de tal manera que el nucli sàpiga on tinc el nou /home a l'hora d'arrencar, com diu papapep?


Buuuuuffff....res de fer enllaços simbòlic pel /home....això no té sentit en aquest cas. És embolicar la troca.

Cal que iniciis l'ordinador amb un livecd, per poder remenar el teu disc dur i moure coses sense tenir el sistema de fitxers muntat. Ara, que si ja has copiat les dades, t'ho pots estalviar.

Tampoc cal formatar per a res la partició del sistema operatiu. El que cal és esbrinar la UUID, sinó la saps ja, de la teva nova partició.

Cal que facis:

```
sudo vol_id -u /dev/sdX
```

essent X el nombre de la nova partició. Ara que li has passat dades, on la tens montada? vull dir, a quin directori li passes els fitxers?

---

### Post by jinglada on 2008-12-02
Gràcies papapep

> **papapep said:**
> Buuuuuffff....res de fer enllaços simbòlic pel /home....això no té sentit en aquest cas. És embolicar la troca.

Em pots explicar -amb la finalitat d'aprendre- per què un enllaç simbòlic és embolicar la troca? 

> Tampoc cal formatar per a res la partició del sistema operatiu.

Volia dir que si en algun moment la meva inexperiència provoca la necessitat de reinstal·lar l'Ubuntu, no perdés las dades.

> El que cal és esbrinar la UUID, sinó la saps ja, de la teva nova partició.

Cal que facis:

```
sudo vol_id -u /dev/sdX
```

essent X el nombre de la nova partició. 

La UUID és:
joan@joan-laptop:~$ sudo vol_id -u /dev/sda5
5de44525-5115-4e83-8af3-9af0102ab58b

> Ara que li has passat dades, on la tens montada? vull dir, a quin directori li passes els fitxers?

La tinc muntada a /media/disk on hi vaig traslladar els directoris que tenia a /home/joan

---

### Post by papapep on 2008-12-02
> Em pots explicar -amb la finalitat d'aprendre- per què un enllaç simbòlic és embolicar la troca?


Els enllaços simbòlics són, per a que m'entenguis, com un enllaç a l'escriptori del windows. M'explico? Les particions i els seus punts de muntatge s'han de definir a l'fstab, deixant clar el sistema de fitxers i la seva estructura. Cada cosa per a la seva funció.
Si no vols moure el /home, i utilitzar el /media/disk com a magatzem de dades en general, sense més, també és una opció. En aquest cas sí que no hi ha problema en emprar un enllaç simbòlic per accedir a /media/disk.

---

### Post by open-pitu on 2008-12-02
La primera resposta, explicava les dos opcions (enllaç simbòlic, modificar punts de muntatge) amb exemples inclosos. No es tractava d'embolicar la troca o no embolicar-la.

Al final s'han acabat donant les dues opcions iniciala, fer un enllaç del home al punt de muntatge o sinó canviar el punt de muntatge a /etc/fstab.

---

### Post by jinglada on 2008-12-02
Gràcies a tots dos pels vostres missatges. Llegint-vos a tots dos em sembla que n'aprendré més depressa. La diversitat de maneres d'explicar-se és enriquidora, almenys per a mi. A veure si ho he entés bé.

1) Si vull fer un enllaç simbòlic (soft-link), en el meu cas he de fer:
```
ln -s /media/disk /home/joan
``` 

¿però llavors al guardar un fitxer de les aplicacions que et porten directament al /home/joan quedarà de fet gravat al directori /media/disk?

2) Si vull muntar el /home a la partició /dev/sda3 hauria de modificar al /etc/fstab la següent línea

```
#Entry for /dev/sda3 :
UUID=208e6e73-641d-43f6-af8b-4b4495f62a58 /media/disk ext3 defaults,nosuid,nodev,uhelper=hal 0 2
```

canviant /media/disk per /home/joan?

---

### Post by open-pitu on 2008-12-03
Exacte. Tot i així, per tenir un millor ordre (si més no mental) tant l'enllaç simbòlic com si retoques fstab jo et recomenaria fer-ho a /home/pitu/dades

Així no tindràs cap mena de problema com el que estàs plantejant i et serà igual d'útil perquè des del teu home tindràs un ràpid accés a les dades que tens a la teva partició de dades (que diria que és el que vols).

Ara un pregunta, perquè tens aquesta partició com a ext3? Tens samba muntat? Si no és així t'aniria millor tenir-la FAT o NTFS per tal de que quan entris en Windows (si és que mai pot ser el cas) tenir-hi també accés.

---

### Post by jinglada on 2008-12-03
Veus com ja ho deia, de la diversitat d'opinions s'aprenen moltes coses. Quan vaig particionar el disc per primera vegada vaig fer dues particions per a dades, una ext3 i una altra NTFS (Pots veure [http://ubuntuforums.org/showpost.php?p=6259597&postcount=12](http://ubuntuforums.org/showpost.php?p=6259597&postcount=12)) i en el següent post, papapep em pregunta per què ho havia fet i com que m'havia fet un embolic entre windows i mac vaig ajuntar les dues particions en una amb format ext3. Si mai necessito windows puc tornar a particionar, oi? No tinc samba muntat. Quins avantatges té muntar-lo?
Encara estic pensant si fer l'enllaç o si munto el /home a la partició.
Gràcies.

---

### Post by open-pitu on 2008-12-04
La idea de samba és fer accessible el sistema de fitxers d'UNIX per la xarxa (i per tant des de Windows).

Et passo l'enllaç de la wikipedia: [http://ca.wikipedia.org/wiki/Samba](http://ca.wikipedia.org/wiki/Samba)

---

