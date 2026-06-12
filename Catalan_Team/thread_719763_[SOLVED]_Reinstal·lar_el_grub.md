---
title: "[SOLVED] Reinstal·lar el grub"
date: 2008-03-09
forum: Catalan Team
---

### Post by Curial on 2008-03-09
Déu vos guard a tots i totes,

No m'arrenca el grub.

Tenia una partició amb un Windosws 98 i l'altre amb l'Ubuntu, i feia temps que volia instal·lar en comptes del W98 un XP.

He instal·lat l'Xp sobre la partició on tenia el W98 i cada cop que arrenco l'ordinador el grub no m'apareix.

He suposat que a l'instal·lar l'Xp me l'ha trepitjat.

No se si necessito un CD alternate de l'Ubuntu per instal·lar el grub sense que em toqui res de la partició on tinc l'ubuntu.

Què em recomanarieu bons companys?

Salut.

---

### Post by patrickfromspain on 2008-03-09
amb un live cd es molt facil:

Obres un terminal i hi entres sudo grub.

Ara has de fer: 

root (hd0,4) (Suposant que tinguis ubuntu a la 5a particio del primer disc dur)
setup (hd0)
exit 

i ja pots reiniciar. Si ho has fet tot be, el grub hauria d'estar reinstal·lat.

salut!

---

### Post by menut on 2008-03-09
Si la instal·lació la fem amb particions primàries, en aquestos casos ens serà molt més fàcil d'identificar on tenim cada sistema operatiu ;)

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")


PS: ja se n'ha parlat d'aquest tema [aquí]("http://ubuntuforums.org/showthread.php?p=4446920#post4446920").

---

### Post by papapep on 2008-03-09
[http://ubuntuforums.org/search.php?searchid=37581239](http://ubuntuforums.org/search.php?searchid=37581239)

---

### Post by Curial on 2008-03-09
Ei perdoneu el que no hagi cercat bé abans, sé que és una cosa que s'ha de fer abans de diparar indiscriminadament les pregunetes.:):)

Tenia problemes perquè no muntava la partició on tenia l'ubuntu i m'he fet una mica l'embolic amb el numero de les particións però m'ha anat de perles amb això:
$ sudo grub                --> ejecutamos el interprete de comando de grub
> find /boot/grub/stage1   --> busca donde esta la partición de ubuntu
> root (hdX,Y)             --> poner el valor devuelto anterior
> setup (hd0)              --> instala grub en nuestro primer disco duro (hd0), 
                               que es con el que inicia la computadora
> quit                     --> salimos del interprete de comando de grub

Altre cop: gràcies per la vostra paciència.

Salut.

---

### Post by orestesmas on 2008-03-10
Això de
```
find /boot/grub/stage1
```

no sempre funciona. Si tens el /boot muntat en una partició a banda llavors has de fer
```
find /grub/stage1
```

---

