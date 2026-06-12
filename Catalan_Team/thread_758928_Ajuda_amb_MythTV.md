---
title: "Ajuda amb MythTV"
date: 2008-04-18
forum: Catalan Team
---

### Post by lluisanunez on 2008-04-18
Hola,
Estem intentant configurar MythTV per funcionar amb una antena que, en principi, Ubuntu reconeix a jutjar per lsusb i dmesg.
Però els problemes semblen més aviat relacionats amb el mysql , perquè no reconeix l'usuari entrat a la configuració. 
Els tutorials que hem trobat fan un sudo dpkg-reconfigure mythtv-database, però això ens dóna el següent error:
```
gina@ubuntu:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Access denied for user 'mythtv'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

```Per canviar el password d'aquest usuari mythtv es necessita ser root?

---

### Post by papapep on 2008-04-18
Ja heu verificat primer el que diu, que el servidor (mysqld) amb el que intenteu connectar estigui realment funcionant ?

> Per canviar el password d'aquest usuari mythtv es necessita ser root? 

Per a canviar els permisos o contrassenya d'un usuari de mysql has de ser o root o un usuari administrador de mysql (igual que amb gnu/Linux, vaja).

Es pot fer tant des de dins el prompt de Mysql:

```
SET PASSWORD FOR 'usuari'@'hostname' = PASSWORD('contrassenya');
```

(molt de compte amb no oblidar el ";" al final de la sentència, sinó no funciona)

com des de l'intèrpret d'ordres d'Ubuntu:

```
mysqladmin -u usuari -p password contrassenya
```

(però en aquest últim cas has de saber l'antiga contrassenya per a donar-n'hi una de nova).

---

### Post by CarlesOriol on 2008-04-19
Hola Lluisa.

Jo tinc el mythtv configurat en dos ordinadors (vig jubilar tots els dvds anteriors).

Primer et recomano que provis la capturadora de dvb amb algun programa que sigui bastant immediat. Ppots usar el **kaffeine** o en hardy  **mt-tv**. Es probable que hagis de cercar firmware privatiu o recompilar els controladors (hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)). No és massa traumàtic i acostuma a funcionar, però en molts casos no és immediat.
Pots saber-ho exactament fent un dmesg després de connectar el dispositiu i veure si et crea coses a /dev/dvb o et diu que et falta algun .fw 

Sobre el que demanes al mythtv pots canviar la password que emmagatzema de configuració manualment al /**etc/mythtv/mysql.txt.** i un cop insta&#320;lat pots fer-ho amb el **mythtv-setup** (on hauras de configurar totes les targetes, canals i mandangues)

---

### Post by lluisanunez on 2008-04-19
Moltes gràcies als dos. No és un ordinador meu (és d'una amiga conversa a Ubuntu) i per tant de moment no ho puc provar. Ja us diré

---

