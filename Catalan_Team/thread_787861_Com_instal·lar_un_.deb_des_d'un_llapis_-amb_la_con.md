---
title: "Com instal·lar un .deb des d'un llapis -amb la consola-?"
date: 2008-05-09
forum: Catalan Team
---

### Post by lo gambusí on 2008-05-09
Salut!!

Com podeu llegir [aquí]("http://ubuntuforums.org/showpost.php?p=4902497&postcount=30") vull instal·lar el controlador de la targeta gràfica des d'un llapis USB amb la consola (des del Recovery Mode). No sé per què, però, no puc fer-ho. Alguna idea de què faig malament?

>  cd /media/KINGSTON_
(perquè és lo nom en lo qual me surt l'usb al meu ordinador) i me diu
> bash: cd: KINGSTON: No such file or directory

Gràcies!:)

---

### Post by papapep on 2008-05-09
Aquí:
> cd /media/KINGSTON[COLOR="Red"]**_**[/COLOR]

i aquí:

> bash: cd: KINGSTON: No such file or directory

no posa el mateix. Difereixen en un guió baix.

Mostra'ns el que et surt en fer un 

```
ls -la /media
```

---

### Post by lo gambusí on 2008-05-09
Em diu això:

> drwxr-xr-x  3 root root 4096 Apr 29 15:44 .
drwxr-xr-x 21 root root 4096 Apr 29 15:54 ..
lrwxrwxrwx  1 root root    6 Apr 29 15:44 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 Apr 29 15:44 cdrom0

---

### Post by papapep on 2008-05-09
Tenies el llapis posat quan ho has fet?? De ser que no, posa'l i torna-ho a fer.

---

### Post by lo gambusí on 2008-05-09
Sí, sí.

---

### Post by papapep on 2008-05-09
"Sí, sí" vol dir que el tenies posat quan ho has fet??? Doncs mentre el tens posat, ves a Llocs > Ordinador a veure si t'hi surt la unitat per muntar o no.
Si no t'hi apareix sembla que l'ordinador no et reconeix el llapis i, aleshores, no sé d'on has tret lo de /media/KINGSTON, però fent el "ls -la" no hi surt pas sota /media.

---

### Post by lo gambusí on 2008-05-09
Sí, el tenia posat quan ho he fet. 

No puc anar a Llocs/Ordinador, perquè estic en Recovery Mode com a Root i no tinc entorn gràfic sinó que és la consola. Estic així perquè no puc entrar en mode gràfic i no tinc connexió a internet.

Lo de media/KINGSTON/ ho he tret de mirar quina ruta té el llapis a un altre ordinador amb Ubuntu.

No sé si m'he explicat...

---

### Post by papapep on 2008-05-09
....i amb el driver vesa (mode gràfic segur es diu?) no pots executar les X?

---

### Post by lo gambusí on 2008-05-09
No entenc què vols dir, ho sento. :|

---

### Post by papapep on 2008-05-09
Quan s'engega l'Ubuntu no t'apareix una opció que es diu "mode gràfic segur" per arrencar? Crec que abans sortia. O potser és al live-cd?
En tot cas, potser et seria més simple posant-hi un live-cd, copiant el fitxer del pendrive al disc dur i després tornar a iniciar com ara i fer la instal·lació.

---

### Post by lo gambusí on 2008-05-09
EDITO: Hi ha un problema, i és que estic usant l'Ubuntu Alternate. Per tant, el live CD no té instal·lació gràfica...

---

### Post by cossier on 2008-05-10
Intenta el següent..:

> init 3

Això detecta la resta de maquinari i podràs comprovar si ha detectat el llapis¡¡

---

### Post by lo gambusí on 2008-05-10
gràcies als dos, ho provaré diumenge, que no tinc l'ordinador aquí... ;)

---

### Post by RainCT on 2008-05-10
No és el que preguntes, però per si algú troba aquest fil buscant com insta&#320;lar un .deb des de la terminal (què és el que s'enten a partir de la pregunta del títol), això és fa amb «sudo dpkg -i fitxer.deb». Per a veure la informació sobre el paquet (de forma similar a com s'aconseguiria amb un «apt-cache show <paquet>» o «aptitude show <paquet>») es pot utilitzar «dpkg -I fitxer.deb» (aquí amb la I majúscula), i finalment per veure el contingut d'un paquet hi ha l'ordre «dpkg --contents fitxer.deb».

---

### Post by sianeu on 2008-05-11
El problema que em trobo amb el Hardy es que posa les particions del disc dur (tant les ext3, com les fat32, com les ntfs) com a "medis extraibles" i sense muntar. Aleshores si vaig a Llocs/Medis extraïbles/discX i el clico, el munta (i apareix a l'escriptori). A partir d'aquest moment si el torno a clicar a Llocs o al escriptori ja s'obre.

Penso que si arranques el ordinador amb el llapis connectat potser no t'el munta. Prova a engegar l'ordinador i desprès connecta el llapis.

---

### Post by Curial on 2008-05-12
> **lo gambusí said:**
> Salut!!

Com podeu llegir [aquí]("http://ubuntuforums.org/showpost.php?p=4902497&postcount=30") vull instal·lar el controlador de la targeta gràfica des d'un llapis USB amb la consola (des del Recovery Mode). No sé per què, però, no puc fer-ho. Alguna idea de què faig malament?


(perquè és lo nom en lo qual me surt l'usb al meu ordinador) i me diu


Gràcies!:)

Hi tens l'espai entre cd i /media quan ho escrius a la línia de comandes?

Si ho escrius tot junt és normal que doni aquest missatge.

---

