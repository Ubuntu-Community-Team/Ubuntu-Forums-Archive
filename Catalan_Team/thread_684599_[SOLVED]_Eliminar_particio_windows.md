---
title: "[SOLVED] Eliminar particio windows"
date: 2008-02-01
forum: Catalan Team
---

### Post by 5froi on 2008-02-01
tinc ubuntu 7.04 fins ara tot perfecte, però voldria eliminar la partició de windows per deixar-la tota per ubuntu.
He de dir que el windows va quedar corrupte. He probat amb Gparted, pero no puc redimensionar les particions, nomes les deixa fer mes petites no mes grans.
Gracies

---

### Post by pespin on 2008-02-01
Diria que primer cal carregar-se la partició de windows i deixar-la com a no formatejada, buida. Llavors suposo que si et deixarà ampliar-la :)

---

### Post by 5froi on 2008-02-01
Ja ho he fet, tampoc em deixa. El Qtparted no em deixa instalar-lo al meu tipus d'ordinador.

---

### Post by Daerun on 2008-02-01
Jo vaig reduir el tamany de la partició windows per cedir espai a la d'Ubuntu amb el LiveCD de Gparted ([AQUI]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") es poden descarregar totes les versions). El que has de fer és arrencar l'ordinador des d'aquest CD; en el meu cas, que tinc Gutsy, no em va funcionar la versió més recent i en vaig haver de fer servir una de més antiga (si no recordo malament, la versió 3.3.5).

---

### Post by papapep on 2008-02-01
5froi: un cop l'hagis eliminat amb el gparted, qtparted, cfdisk o el que vulguis, la podràs "afegir" al teu sistema de fitxers muntant-la al directori (punt de muntatge) que et plagui. No cal que juntis les particions per a que "siguin" de l'Ubuntu.

Hi ha un live cd molt útil que es diu [systemrescuecd]("http://www.sysresccd.org/Main_Page") el qual et permetrà manegar com vulguis les particions (i moltíssimes coses més).

---

### Post by Daerun on 2008-02-01
Això és interessant, però no ho he entès... Què vol dir això de que es pot muntar en un directori?

---

### Post by papapep on 2008-02-01
Doncs que a linux, quan s'utilitzen particions es munten a un, valgui la redundància, punt de muntatge. Si vas a un terminal i hi fas:

```
cat /etc/fstab
```

veuràs que se't mostra alguna cosa semblant a això:

> # /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=08deb52b-14ec-4c53-98b4-03901b8d8373[COLOR="Red"]** /**[/COLOR] ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=420e5c45-a939-4838-988e-f6bf10197785 [COLOR="Red"]**/home**[/COLOR] ext3 defaults 0 2
/dev/sda2       /home/papapep/gravacio_tdt ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=c291f848-20dc-4055-9652-b2dd61ddb4b4**[COLOR="Red"] /usr[/COLOR]** ext3 defaults 0 2
# Entry for /dev/sda7 :
UUID=26790e07-6af1-484d-a0fe-2d6d7bb4a985 none[COLOR="Red"]** swap**[/COLOR] sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/sdb1 /media/disk ntfs-3g defaults,locale=ca_ES.UTF-8@euro 0 0

Aquí veureu que hi ha quatre particions: sda3, sda6, sda5 i sda7.
La última, la swap la de intercanvi, és d'un tipus especial i no en parlarem.
Les tres primeres, es munten als punts del sistema de directoris que he remarcat en vermell.
sda3 comença (es munta) a l'arrel (/)del sistema de fitxers (per a entendre una mica la estructura dels sistemes de fitxers a linux aconsello una repassadeta a [aquest)]("http://extralinux.net/?q=node/6") [i aquest]("http://extralinux.net/?q=node/30") articles), sda6 es munta a /home, i sda7 a /usr.

O sigui, en el moment que clico amb el ratoli sobre un fitxer que és dins /home realment estic accedint a dades que són a la partició sda6 del meu disc dur. Si executu un fitxer que sigui a /usr/bin, per exemple, estic accedint a dades que són a sda7, etc...
Tot això, evidentment, de manera completament transparent per a l'usuari.

Espero haver-me explicat. Si no ha estat així, ja preguntareu el que calgui.

---

### Post by 5froi on 2008-02-01
MOOOLT BE, he fet servir el system rescue cd i perfecte, ha surtit el gparted versio 0.3.4 i la del livecd era 0.2.5.
Ha anat perfecte.
Moltes gracies.

---

