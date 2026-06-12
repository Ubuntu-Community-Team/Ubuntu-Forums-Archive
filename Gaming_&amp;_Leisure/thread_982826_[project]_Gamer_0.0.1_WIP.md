---
title: "[project] Gamer 0.0.1 WIP"
date: 2008-11-15
forum: Gaming &amp; Leisure
---

### Post by Dinth on 2008-11-15
Hello all. I want to trot out about my app, which i started to code to learn programming, but also i see some progresses in this project development and propably it will see world someday:), so i writing this post to learn about your opinions and ideas, which maybe i will can implement.

Gamer will be modern and simple (everyone will can use it with few mouse clicks, and without knowing words like MAME, Tosec, or rom), integrated with GNOME, multi-emulator front-end.

In first versions (up to 0.2.x) i want to achive only some good state of MAME frontend, so up to then Gamer will support only arcade machines emulation.

Gamer is writen in python with use of such libraries as: Gtk, Glade, libxml, sqlite, gconf and others.

URL - launchpad: [http://launchpad.net/gamer](http://launchpad.net/gamer)
URL - screenshots from 0.0.1 WIP: [http://s404.photobucket.com/albums/pp121/DinthKSC/Gamer%20v001%20WIP/](http://s404.photobucket.com/albums/pp121/DinthKSC/Gamer%20v001%20WIP/)
URL - future project website: [http://www.making-dreams.pl](http://www.making-dreams.pl)

What is done up to today (15 november):

- most of simple GUI
- simple rom list refresh
- sqlite games database

TODO version 0.1.x:

- clean up the code, now its a little bit trashy
- bugfixes
- add locale support in PO files
- showing games information
- basic MAME configuration options/tweaks

Please send my all kinds of contributions, ideas and opinions in this topic or at the email: [dinth AT wikipasy DOT pl].

Version 0.0.1 download (Attention - this version isnt meant to be playable/useful or even working and it is in polish language - use at own risk): [http://www.making-dreams.pl/Gamer-0.0.1.tar.gz](http://www.making-dreams.pl/Gamer-0.0.1.tar.gz)

---

### Post by Nevon on 2008-11-15
The link to the screenshot is broken.

---

### Post by Dinth on 2008-11-15
Ive fixed screenshot link and added to gallery two new screenshots with today progress.

---

### Post by Dinth on 2008-11-15
Version 0.0.1 is out. It isn't meant to be playable/useful/or even working, and it is now in polish language only: [http://www.making-dreams.pl/Gamer-0.0.1.tar.gz](http://www.making-dreams.pl/Gamer-0.0.1.tar.gz).
 
Please also remeber that i'm learning programing, so dont bother in bugs/ugly code and please send me contributions and code advices :)

---

### Post by Changturkey on 2008-11-15
Good job.

---

### Post by Dinth on 2008-11-16
0.0.2 version is expected in few days, and will be in english with gettext support. [false]No expected bugfixes[/false], as repairing one irritating bug of which i know (Popen freezes GUI when refreshing games list) is like black magic for me, and currently i dont know how to fix it (any advices?). [there will be bugfixes. today ive looked on application in perspective of user, and saw that Gamer hase so much bug like cheese with holes ;) ]

0.0.3 version will feature code cleanup to: 1. make it clean :); 2. make use from OO, and also automatic mame executable searching (with whois command) and xmame support

---

### Post by Abras on 2008-11-16
This sounds like a great idea. Emulators have always a bit inaccessible to newer computer users and the problem doubles with the emulators for Linux. There are some emulators that don't even have GUIs. And among those that do the GUIs to be a bit poorly done and a lot projects keep the GUI and the main program separate for some reason. I know this project really won't fix these problems, but I do think it will make it easier for novice and experienced users alike to enjoy video game emulation on Linux.

So I say keep up the good work and I'd be happy to help you with any writing aspects.

---

### Post by Dinth on 2008-11-18
0.0.2 is out! :)

[http://www.making-dreams.pl/Gamer-0.0.2.tar.gz](http://www.making-dreams.pl/Gamer-0.0.2.tar.gz) - tar.gz
[http://www.making-dreams.pl/Gamer-0.0.2.deb](http://www.making-dreams.pl/Gamer-0.0.2.deb) - deb (might be not working;) 

Changelog:
```

- Gamer is now in english
- gettext support for localizations [Isnt working with Glade strings - dont know why ATM]
- fixed detection of rom status checking
	- Gamer no longer halts when roms path is empty
	- Gamer now dont (or at least shouldn't;) ) show incorrect/unexisting roms on list 	
- dialogs classes now use configuration data from Gamer class, not own
- refreshing games list Treeview after refreshing games list moved to RefreshDialog class [this code is slighty broken, it will be moved back to Gamer class and fixed in 0.0.3]
- fixed checking if selected row on Games list is actual game
	- clicking "Play!" on "Arcade games" no longer crashes Gamer
	- its possible to play first game on the list
- Gamer is now installable - added Makefile 
- sqlite database is now in users ~/.Gamer directory
- .deb package [might be broken - i didn't tested this]

```

---

### Post by binbash on 2008-11-18
I am gonna test it when version 0.03 is out.

---

### Post by Dinth on 2008-11-26
0.0.3 will be propably released after Christmas. But if it will be completly stable, it will be last version supporting only MAME and after it i'll start 0.1.0 branch.

---

