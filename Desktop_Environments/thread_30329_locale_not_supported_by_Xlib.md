---
title: "locale not supported by Xlib"
date: 2005-04-28
forum: Desktop Environments
---

### Post by desheikh on 2005-04-28
Hi,

Every time I run just about any program through the terminal it gives me this warning:

(gedit:15649): Gdk-WARNING **: locale not supported by Xlib

(gedit:15649): Gdk-WARNING **: cannot set locale modifiers

My program still works.. but im confused as to whats wrong :S

If someone knows how to solve this please hepl me out :)

Ali

---

### Post by shimon on 2005-04-28
File a bug in bugzilla

---

### Post by desheikh on 2005-04-28
I would but I dont know how :P... havnt been using linux that long now..

---

### Post by cutOff on 2005-05-09
[QUOTE=desheikh]Hi,

Every time I run just about any program through the terminal it gives me this warning:

(gedit:15649): Gdk-WARNING **: locale not supported by Xlib

(gedit:15649): Gdk-WARNING **: cannot set locale modifiers

My program still works.. but im confused as to whats wrong :S

If someone knows how to solve this please hepl me out :)

Ali[/QUOTE]
I'm having same issue.

Here's my locales

```
cutoff@this:~$ locale
LANG=es_ES.UTF-8@euro
LC_CTYPE="es_ES.ISO-8859-1 "
LC_NUMERIC="es_ES.ISO-8859-1 "
LC_TIME="es_ES.ISO-8859-1 "
LC_COLLATE="es_ES.ISO-8859-1 "
LC_MONETARY="es_ES.ISO-8859-1 "
LC_MESSAGES="es_ES.ISO-8859-1 "
LC_PAPER="es_ES.ISO-8859-1 "
LC_NAME="es_ES.ISO-8859-1 "
LC_ADDRESS="es_ES.ISO-8859-1 "
LC_TELEPHONE="es_ES.ISO-8859-1 "
LC_MEASUREMENT="es_ES.ISO-8859-1 "
LC_IDENTIFICATION="es_ES.ISO-8859-1 "
LC_ALL=es_ES.ISO-8859-1
``` 
Does anybody know what can be??

---

### Post by humina on 2005-09-16
If you type locale -a you will note that es_ES.ISO-8859-1 is not on the top.  That's your problem right there.  I have no idea how to fix it though.

---

