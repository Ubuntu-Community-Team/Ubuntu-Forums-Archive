---
title: "making a .deb package?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by sickdude on 2005-11-08
i wanted to know how to make a .deb package

i just installed proftp (isnt in the repo :() and i want to make a .deb package so i can install it the easy way, including my own config file. i know how to do the ./configure and the make, make install but i really dont have a clue how make it in a custom .deb package 

any help would rule

thnx in advance :D

---

### Post by Susana on 2005-11-08
[QUOTE=sickdude]i wanted to know how to make a .deb package

i just installed proftp (isnt in the repo :() and i want to make a .deb package so i can install it the easy way, including my own config file. i know how to do the ./configure and the make, make install but i really dont have a clue how make it in a custom .deb package 

any help would rule

thnx in advance :D[/QUOTE]

Hi!

Look here:
[http://www.ubuntuforums.org/showthread.php?t=2356](http://www.ubuntuforums.org/showthread.php?t=2356)

or here:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by Pablo_Escobar on 2005-11-08
Install a package called "checkinstall" via synaptic or apt-get.
Then when You compile, You:
1. ./configure
2. make
3. sudo checkinstall -D   (it'll create a nice *deb package which You can install) works like a charm.

---

### Post by sickdude on 2005-11-08
w00t that works like a damn charm

thnx loads :D

using linux was never this easy i think :P

---

### Post by HermanAB on 2005-11-08
Making debs and rpms was black magic until checkinstall came along.  

Note that Checkinstall doesn't handle Perl quite right.  So for Perl modules, you have to run perl2rpm, then convert to deb using alien.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by Kyral on 2005-11-08
Note: Checkinstall is considered a hack. Its alright if you just want to make packages for yourself, but if you intend to distribute them, then please do it the right way via the Debian New Maintainers Guide

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by dentaku65 on 2005-11-08
You can use Alien
[http://yep.it/?z7vcd5](http://yep.it/?z7vcd5)
it is in the repo too...

---

### Post by kakashi on 2005-11-09
checkinstall is a bad programs. 
it screwed up my compilation of both wine and mplayer.
don't use it.

---

### Post by Kyral on 2005-11-09
[QUOTE=kakashi]checkinstall is a bad programs. 
it screwed up my compilation of both wine and mplayer.
don't use it.[/QUOTE]
Hooray! Someone who saw the light (I apologize about my attitude towards CheckInstall, but if everyone knew the proper way to make debs the world would be a better place :D)

---

### Post by Pablo_Escobar on 2005-11-09
Kyral, I checkinstalled some packages and they work fine. I don't distribute them I just want my system clean.
But on the other side I'll have to look into how it should be done the proper way :)

---

### Post by go_beep_yourself on 2007-10-29
Checkinstall doesnt work for wxDownloader. How can a deb package be created for gutsy?

---

