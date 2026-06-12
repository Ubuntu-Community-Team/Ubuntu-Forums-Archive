---
title: "Flickering Flash Games"
date: 2010-04-21
forum: Gaming &amp; Leisure
---

### Post by bluesmok on 2010-04-21
Most flash games that I run in either Firefox or Chrome flicker black  and white bars across them constantly.  Additionally, clicking or  pressing buttons in-game are sometimes non-responsive. 
I'm quite new to Linux, if anyone could help me out with this problem,  I'd be much appreciative.

---

### Post by I8NY on 2010-04-22
flickering and not responding to clicks, sounds like your trying to use flash in 64bit Ubuntu.  This is a common problem and adobe has a 64bit version that is in beta that will fix most(or all) the problems.     	Download [this]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz"), 	 	 	 	then place the extracted file in   	 	 	 	 	  “[FONT=Times New Roman, serif]/usr/lib/mozilla/plugins/”. [/FONT] If you install the extras(flash,java, etc.) in the software center then this will not work until the flashplugin-installer is removed.  Hope this works and you enjoy Ubuntu.

---

### Post by bluesmok on 2010-04-22
Yes, I am running 64bit Ubuntu.  However, I tried what you suggested, and now every time I go to a page that has a flash video or game, Firefox instantly crashes.  I'm using the newest version of Firefox, 3.6.3, if that makes any difference...

---

### Post by I8NY on 2010-04-22
did you remove the current version of flash before install the 64bit version?

---

