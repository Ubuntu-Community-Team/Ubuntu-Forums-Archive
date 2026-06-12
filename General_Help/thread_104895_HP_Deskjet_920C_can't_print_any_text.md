---
title: "HP Deskjet 920C can't print any text"
date: 2005-12-17
forum: General Help
---

### Post by Tyltyl on 2005-12-17
Hello all, this is my first message here. I'm afraid that it's about an annoying problem :???: 

I have used Ubuntu breezy 5.10 for a few weeks now with little (but solvable) problems, so I'm happy with it now. I only have a problem that I can't solve.
I have installed my HP Deskjet 920C (parallel port) with hpijs drivers and I can print just fine. Graphics are ok, links are fine, but I can't seem to print any text at all. Let's say that if I print this page I can see the banners and the underlined URL's, but the normal text doesn't appear on the printed page.

Why do I have this problem?
I tried using other drivers without any success. I installed Gimp-print, but I can only use the hpijs. I tried installing other filters, but it didn't solve my problem. 
My black cartridge is ok because I can print on Windows XP and if I print graphics on B/W everything appear ok.

I searched all the web and I found some people with the same problem but nobody ever answered :(

It's driving me crazy, what can I do?

EDIT: I tried printing an email and it even prints the signature, but not the header and the main text! It's crazy!

---

### Post by kosmic on 2005-12-17
Just a very very silly question...but do you have black ink in our printer ?? it can be the problem :)

---

### Post by Tyltyl on 2005-12-17
Yes I have, not the first time I get this suggestion :)
I can print graphics in black and white, and on Windows XP it works ok. 

It's just the text that doesn't get recognized in some ways...

---

### Post by kosmic on 2005-12-17
very strange problem, HP printers in Linux are well suported
 
linuxprinting.org - [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_920C]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_920C")
 
 
Just try to use **HPLIP **instead of **HPIJS**

---

### Post by Tyltyl on 2005-12-17
I have them, but when I choose "install driver..." and I go into the hplip folder I choose the right driver but I see it listed as hpijs and nothing changes.
Whatever I do I can only choose hpijs drivers :(

I tried to install Gimp-Print but after the installation I don't know what to do, there's no application to open and I don't know where are the drivers to choose.

---

### Post by Tyltyl on 2005-12-17
I just found out that there's really a problem with the black ink cartridge despite it's full.
For some reason the printer doesn't use it under Linux.

---

