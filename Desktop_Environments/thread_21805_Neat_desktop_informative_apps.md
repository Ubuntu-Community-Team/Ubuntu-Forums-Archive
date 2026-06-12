---
title: "Neat desktop informative apps"
date: 2005-03-24
forum: Desktop Environments
---

### Post by wbeck85 on 2005-03-24
I have noticed that many screen shots include very cool looking apps on the desktop that give information such as system information, calendars, a whole host of goodies. How might i get these wonderful tools for Kubuntu? are they available via apt-get?

---

### Post by apokryphos on 2005-03-24
I think you're referring to superkaramba. You can install the program from the repositories (sudo apt-get install superkaramba), but the themes you'll have to get from elsewhere. 

By far the best site for this on the Internet (and unrivalled, in general, for KDE eye-candy) is [www.kde-look.org](www.kde-look.org) Scroll down to the "Karamba" section.

---

### Post by bnutting on 2005-03-24
I think you may also be referring to gdesklets. I had played with them a little with Warty, but now that I'm running Hoary I have not tried them. Maybe someone with a  little more knowledge that the me could chime in.

Bryan

---

### Post by lao_V on 2005-03-24
gdesklets, being a gtk app, is best suited for GNOME whereas superkaramba is best suited for KDE.

---

### Post by dermotti on 2005-03-24
I got superkaramba on my desktop

[http://www.rateasia.com/kub3.jpg](http://www.rateasia.com/kub3.jpg)

---

### Post by wbeck85 on 2005-03-25
[QUOTE=lao_V]gdesklets, being a gtk app, is best suited for GNOME whereas superkaramba is best suited for KDE.[/QUOTE]
 Thanks guys. I think I will try them both out. I'm running both Windows Managers, depending on the way I feel.

---

### Post by wbeck85 on 2005-03-25
What do I do about these LMSensors? Are they already installed? How do I put the info desklets on my desktop (using gdesklets) ? I really want the sys/cpu info like voltatges, freq, fanspeed, etc

---

### Post by uberlinux on 2005-03-31
anyone else have trouble with gdesklets???
they keep on moving on every reboot, and are unmoveable to get them back in the right place.  they also seem to crash often and eat recources

---

### Post by KongeOdin on 2005-04-07
Apt-get is getting me an old install I think.
The newest version that uses many of the themes are superkaramba 0.35.
Only problem is I cant get it to install.

xxxxx@xxxxx:~/superkaramba-0.35$ ./configure --x-includes=DIR/etc/x11

checking for X... libraries /usr/X11R6/lib, headers DIR/etc/x11
checking for IceConnectionNumber in -lICE... no
checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.

How to do it?
I found the answer myself:                

$ sudo apt-cache search libXext

$ sudo apt-get install xlibs-dev

sorry to bother you.

---

### Post by TjaBBe on 2005-04-07
[QUOTE=uberlinux]anyone else have trouble with gdesklets???
they keep on moving on every reboot, and are unmoveable to get them back in the right place.  they also seem to crash often and eat recources[/QUOTE]
 Yeah I have had some location/starting/hanging problems too. These tools look great on screenshots, but I don't like them verymuch for my own computer, as I haven't seem them stable as of yet.

---

### Post by KongeOdin on 2005-04-14
The last version of superkaramba (0.35)  was recently (With the official release of Hoary Hedgehog) possible to ap-get.  Liquid weather 11(or something)   is now working great on my Kubuntu KDE desktop.

---

