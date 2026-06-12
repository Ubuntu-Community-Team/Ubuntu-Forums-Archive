---
title: "what is needed to play half life 2 under breezy?"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by jabberwocky on 2005-10-13
what is needed to play half life 2 under breezy? 

can i get the retail ati radeon 9600 drivers from the repositories?  

cedega for ubuntu?  

thanks

---

### Post by madjo on 2005-10-13
All I know for certain is that HL2 isn't supported by Linux natively, so yeah you need some sort of emulation layer like Cedega (which is reported to support Steam).

ATI isn't exactly known for quality Linux drivers of their videocards, but I think that using those drivers from the repositories you can get it running. (I'd also suggest you search this forum on 'ATI drivers', might help you)

---

### Post by colours on 2005-10-13
To get ATI drivers, take the following three steps:

1. Run **sudo apt-get install xorg-driver-fglrx**

2. Edit your **/etc/X11/xorg.conf** so that it has a part that looks like this (but with whitespace):

Section "Device"
     Identifier       "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
     **Driver           "fglrx"**
     BusID            "PCI:1:0:0"
EndSection

The important part is that Driver is set to "fglrx", and not "ati".

3. Restart X.

I hope that works fine; it did for me. Bear in mind, however, that ATI's Linux drivers give quite poor performance, and that you'll need [Cedega]("http://www.transgaming.com/") to play *Half-Life 2* as there's no native Linux version of it.

---

### Post by burk on 2005-10-13
Steam works on Cedega, but steam often comes with updates on the platform and on the games and that sometimes cause it to stop working under cedega. Even though the cedega developers quickly fix these problems it is best to use the paid version since you get the updates faster then...

---

### Post by No6 on 2005-10-13
I can confirm that Half-Life 2 works really well with Ubuntu and Cedega. I play it on linux over windows as it seems a bit quicker (because I've turned off pixel shaders... :-) ) The $15 for 3 months subscription is well worth it, especially if you live in the UK with the exchange rates. ;-).

---

### Post by nirtal on 2005-10-13
Try to look at this guide, it use wine so u don't need to buy anything exept the game...
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)

---

### Post by thewebguy on 2005-10-13
[QUOTE=jabberwocky]what is needed to play half life 2 under breezy? 

can i get the retail ati radeon 9600 drivers from the repositories?  

cedega for ubuntu?  

thanks[/QUOTE]

lol are you THE jabberwocky?  we want fragmastarrrr!

---

### Post by poofyhairguy on 2005-10-22
[QUOTE=jabberwocky]what is needed to play half life 2 under breezy? 

can i get the retail ati radeon 9600 drivers from the repositories?  

cedega for ubuntu?  

thanks[/QUOTE]

Not to make you sad, but my 9600 card would not work very good with Cedega.

Thats why my computer has a 6600 GT now. There is nothing wrong with dual booting!

---

### Post by strikeforce on 2005-10-23
[QUOTE=nirtal]Try to look at this guide, it use wine so u don't need to buy anything exept the game...
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)[/QUOTE]

There is a bug with the latest wine but the patch has been committed to the cvs so my recommendation is to use the cvs version or the dx9version.

Btw I use cedega so I can't offer any help or support.

---

### Post by royg1234 on 2005-12-16
how do I play half-life 1?

---

### Post by hampus on 2005-12-17
[QUOTE=royg1234]how do I play half-life 1?[/QUOTE]
You can use wine. Run the installer from the CD with wine. If the installer doesn't work you can install it in windows (if you have windows) first and then copy the files to you linux partition.

---

