---
title: "DvD styler"
date: 2005-12-07
forum: General Help
---

### Post by masterperas on 2005-12-07
i've installed every package avaible in synaptic but i still get this damn error ```
me@mypc:~/Desktop$ sudo dpkg -i dvdstyler_1-1.4-1_i386.deb
Selecting previously deselected package dvdstyler.
(Reading database ... 81151 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1-1.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Package libwxgtk2.4 is not installed.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dvdstyler
```
i dont get it

i tried this 

```
 sudo apt-get install libwxbase2.4-dev libcurl3-dev libgtk1.2-dev libwxgtk2.4-dev

```
and still get the error, help

mind that when i say every, i mean every1 i could logicly link with libwxgtk2.4

---

### Post by nocturn on 2005-12-07
It says it needs libwxgtk2.4 at least at 2.4.3.1, do what version do you have?

aptitude show libwxgtk2.4 should show it.

---

### Post by masterperas on 2005-12-07
[QUOTE=nocturn]It says it needs libwxgtk2.4 at least at 2.4.3.1, do what version do you have?

aptitude show libwxgtk2.4 should show it.[/QUOTE]

```
nuno@peraspc:~/Desktop$ aptitude show libwxgtk2.4
Package: libwxgtk2.4
State: not a real package

```

it seems i dont have it! but the problem is i installed the libwxgtk2.4-1 package

---

### Post by jnie on 2005-12-07
[QUOTE=masterperas]i've installed every package avaible in synaptic but i still get this damn error ```
me@mypc:~/Desktop$ sudo dpkg -i dvdstyler_1-1.4-1_i386.deb
Selecting previously deselected package dvdstyler.
(Reading database ... 81151 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1-1.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Package libwxgtk2.4 is not installed.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dvdstyler
```
i dont get it

i tried this 

```
 sudo apt-get install libwxbase2.4-dev libcurl3-dev libgtk1.2-dev libwxgtk2.4-dev

```
and still get the error, help

mind that when i say every, i mean every1 i could logicly link with libwxgtk2.4[/QUOTE]

Exactly my problem aswell. If you have'nt found it allready try this thread [http://www.ubuntuforums.org/showthread.php?t=58665&page=3]("http://www.ubuntuforums.org/showthread.php?t=58665&page=3")
 and look for post #23, that file installed fine on my system, but DVDstyler crashes with a segment fault:( , as I describe in my post.... a bit annoyed..

Jan

---

### Post by fsman on 2006-01-05
Finally got DVDstyler installed very easily in breezy

just add the following to /etc/apt/sources.list and install dvdstyler via synaptic (you'll have a manually add a menu entry)

deb     [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/)     breezy   main

please refer to the dvdstyler wiki [http://dvdstyler.sourceforge.net/wiki/Installation](http://dvdstyler.sourceforge.net/wiki/Installation)

---

### Post by fsman on 2006-01-05
Finally got DVDstyler installed very easily in breezy

just add the following to /etc/apt/sources.list and install dvdstyler via synaptic (you'll have a manually add a menu entry)

deb     [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/)     breezy   main

please refer to the dvdstyler wiki [http://dvdstyler.sourceforge.net/wiki/Installation](http://dvdstyler.sourceforge.net/wiki/Installation)

also, you need to modify the conf see
[http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError](http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError)
new line should be 
jpegtopnm "$FILE_IN" | ppmtoy4m -n 1 -I t -L $FRAME_RATE -S 420mpeg2| mpeg2enc -f 8 -b $BITRATE -o "$FILE_OUT" $VIDEO_NORM

---

