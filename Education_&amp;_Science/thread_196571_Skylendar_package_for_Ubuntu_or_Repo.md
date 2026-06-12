---
title: "Skylendar package for Ubuntu or Repo"
date: 2006-06-14
forum: Education &amp; Science
---

### Post by brickbat on 2006-06-14
Skylendar seems to be a really nice GUI based astrology program that my wife is begging me for.  I have tried installing it but the dependencies are killing me.  Could someone that knows about these things please package it up for Dapper or even better, put it in the Repo?  I'm sure it would be quite a popular desktop application if it was in the repo because I could only find 1 astrology program in the repo and it was cli based.

Its for KDE and I'm running Gnome but I have no choice because I haven't been able to find a gui Astrology program in Gnome.  I think thats also why I've had so much trouble installing it.  I asked for help with this a long time ago with Hoary I think and I got silence.

Please someone help me.

Thanks
bb

---

### Post by Marle on 2006-06-14
Using KDE programs in Gnome shouldn't be a problem.  I had all sorts of KDE programs running in Gnome before I switched to KDE.

I don't know that much about Skylendar.  I did find this on their website:

Skylendar needs the following packages:
- KDE 3.x
- QT 3.x
- PostgreSQL 7.2.x or 8.x client and server, the plpgsql language plug-in, and probably the QT-PostgreSQL driver
- perl-xml-enno for the skif utility.
- For the compilation and installation processes, the KDE, QT and PostgreSQL development packages must also be installed.

I don't know if you've gone through that list and installed everything, but that would be something to do if you haven't.    

Are you really attached to Skylendar, or are you open to trying any astronomy program?  [Celestia]("http://www.shatters.net/celestia/") looks nice, and it's in the [Dapper Universe]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=celestia&searchon=names&subword=1&version=dapper&release=all").  It even has a gnome frontend.  [Here's]("https://wiki.ubuntu.com/UbuntuScientists/Astronomy") a list of other astronomy programs for Ubuntu, too, if Celestia doesn't float your boat.  I hope you find something you like.  :D

---

### Post by brickbat on 2006-06-16
Well, I'm not attached to Skylendar but I am looking for a gui based **Astrology** program - **not Astronomy** program - so if you have any other suggestions that are easier to install then I would be interested. I tried installing the dependencies on lis page but I still get errors when trying to install it.

---

### Post by brickbat on 2006-06-25
bump!

---

### Post by fraehttt on 2007-03-10
I have got skylendar working on kubuntu feisty. I did use gcc 3.4 and I habe to set xhost +local to be able to start it.

I hope that will help you.

Freddy

---

### Post by kleeman on 2007-03-10
Astrology=Science/Education? :lolflag: 
Maybe you should ask in another subforum.

---

### Post by vanbosco on 2008-02-22
> **brickbat said:**
> Skylendar seems to be a really nice GUI based astrology program that my wife is begging me for.  I have tried installing it but the dependencies are killing me.  Could someone that knows about these things please package it up for Dapper or even better, put it in the Repo?  I'm sure it would be quite a popular desktop application if it was in the repo because I could only find 1 astrology program in the repo and it was cli based.

Its for KDE and I'm running Gnome but I have no choice because I haven't been able to find a gui Astrology program in Gnome.  I think thats also why I've had so much trouble installing it.  I asked for help with this a long time ago with Hoary I think and I got silence.

Please someone help me.

Thanks
bb
Try Maitreya, [http://www.saravali.de/maitreya/index.html](http://www.saravali.de/maitreya/index.html), there's no package for ubuntu but it's simple to install from source.
```
 sudo apt-get install libwxgtk2.8-dev libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 wx2.8-headers wx2.8-i18n wx-common
```
than ./configure, make, sudo make install.
On my system works great. :)

---

### Post by ruipedroca on 2008-08-03
> **vanbosco said:**
> ./configure, make, sudo make install.
On my system works great. :)

In what directory do I have to execute these comands?

Regards

---

