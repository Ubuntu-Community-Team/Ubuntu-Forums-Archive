---
title: "Programes d'inici"
date: 2008-03-04
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-03-04
Bones.
He fet un cop d'ull als programes d'inici que tinc marcats. Estic pensant de treure'n algún per millorar el tems d'arrancada. concretament hi han 3 que no se que son i pot ser algú me ho podria aclarir. 
-tracker
-Update notifier
-User folders update

Moltes gracies.

---

### Post by lluisanunez on 2008-03-04
Tracker és un cercador d'escriptori (idea similar al Google taskbar i al Beagle): documents, contingut de documents, metadades de video i audio... l'indexador pot consumir molts recursos però es pot configurar un límit. De vegades no va massa bé i cal reindexar...

Update notifier és l'avís que t'apareix quan hi ha actualitzacions disponibles (la icona taronja amb una estrelleta blanca)

User folders update encara no sé què és

---

### Post by lluisanunez on 2008-03-04


User folders update: recorda el caché del DOS, oi? amb un índex dels subdirectoris més usats

**Xdg-user-dirs**

 xdg-user-dirs is a tool to help manage "well known" user directories  like the desktop folder and the music folder. It also handles localization (i.e.  translation) of the filenames. 
The way it works is that xdg-user-dirs-update is run very early in the login  phase. This program reads a configuration file, and a set of default  directories. It then creates localized versions of these directories in the users home directory and sets up a config file in $(XDG_CONFIG_HOME)/user-dirs.dirs (XDG_CONFIG_HOME defaults to ~/.config) that applications can read to find these  directories.

[http://www.freedesktop.org/wiki/Software/xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs)

---

### Post by Miquel Ubuntero on 2008-03-05
Ok. Gracies LLuisa.
Hem quedo amb el update, i els altres 2 els treure.
A veure si aconseguim que tiri una mica millor l'ordina.
Salut!

---

### Post by lluisanunez on 2008-03-06
Sí, el trackerd menja memòria, quan es recorda d'indexar

---

