---
title: "Disc extern per Ubuntu quin format per  mes velocitat"
date: 2008-06-15
forum: Catalan Team
---

### Post by manelolesa on 2008-06-15
Hola tinc un nou disc USB extern de 500Gb, no mes el faré servir per l'Ubuntu i el meu dubte es amb quin tipus de format tindre mes rapidesa, amb EXT2,EXT3,NTFS, etc....

Gracies

---

### Post by patrickfromspain on 2008-06-15
mes rapid no se, pero un consell ni FAT32 ni NTFS. Jo tinc un disc dur exter de 120gb i el tinc formatejat en ext3 i em va be.

salut!

---

### Post by orestesmas on 2008-06-15
> **manelolesa said:**
> Hola tinc un nou disc USB extern de 500Gb, no mes el faré servir per l'Ubuntu i el meu dubte es amb quin tipus de format tindre mes rapidesa, amb EXT2,EXT3,NTFS, etc....

Gracies

La FAT32 no suporta permisos de fitxers ni propietari/grup. Si només el fas servir en GNU/Linux, no és recomanable.

El NTFS és un format propietari de Microsoft, i el suport en GNU/Linux sempre serà precari. Ni somniar-ho.

Jo usaria ext3 o XFS, jo diria que el darrer és més ràpid.

Però, escolta, què t'impedeix fer les proves tu mateix? Endolles el disc, hi crees un parell de particions (o més si vols provar més d'un sistema de fitxers), les formateges amb diferents sistemes de fitxers, les muntes en alguna banda, i uses un programa per fer proves de lectura/escriptura a les particions resultants. Per fer les proves pots usar el programa "bonnie++", per exemple.

En acabar, esborres les particions creades i en crees una de sola i la formateges amb el sistema de fitxers que hagis trobat més ràpid.

---

### Post by CarlesOriol on 2008-06-16
Crec que en qualsevol dels casos el coll de botella és l'ample de banda de l'usb.

Per tant, tant l'ordinador organitzant el sistema d'arxius com el disc enregistrant hauran de passar la major part del temps esperant la transferencia per l'usb.

Per tant insta&#320;la aquell sistema que et sigui més còmode per l'us que vols donar-li.

---

### Post by manelolesa on 2008-06-16
De moment amb EXT3 sembla que funciona força be.
Amb NTFS habia observat que feia força us de CPU.

Salutacions

---

### Post by climent on 2008-06-16
Jo estic més amb la línia d'en CarlesOriol. He fet diverses proves amb un disc USB de 300 Gb, endollant-lo a diferents entrades: port USB directe i port USB des d'una tarja PCMCIA. Els resultats són molt similars. La pcmcia i el disc dur poden anar amb USB 2.0, però el meu ordinador és de 1.0, o sigui que a patir amb el coll d'ampolla. Vaig comprar la pcmcia per veure si el dis anava més ràpid, i no. Després va resultar que se'm va espatllar el disc dur, el vaig canviar per un de nou, vaig repetir les proves i els resultats igual. El primer disc el tenia amb FAT, vaig provar FAT32 i EXT3 i tres quarts del mateix. Ara el tinc amb FAT32 i com la seda. ARa, això sí, NTFS ni parlar-ne!!

---

### Post by CarlesOriol on 2008-06-16
> **manelolesa said:**
> De moment amb EXT3 sembla que funciona força be.
Amb NTFS habia observat que feia força us de CPU.


Si sols has d'usar linux ext3 va de conya. 

Si has d'usar també windows tens raó que el controlador linux de ntfs pren molt temps de procesador i llavors millor fer-ho en fat32.

Però dels 3 que hem dit el fat32 no és tolerant a errors per tant en un error és més possible que perdis dades.

Els altres xfs i reiser... crec que ara per ara no val la pena tenint el ext3 i usant ubuntu.

---

