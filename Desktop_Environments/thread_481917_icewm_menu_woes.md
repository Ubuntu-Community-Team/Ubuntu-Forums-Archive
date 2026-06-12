---
title: "icewm menu woes"
date: 2007-06-23
forum: Desktop Environments
---

### Post by jplowman on 2007-06-23
Hello!

I first installed xubuntu, and then icewm with rox-filer, using Peter76's[ very helpful guide]("http://ubuntuforums.org/showthread.php?t=171203").

But icewm's menu file is giving me a headache. I want a "start menu" similar to the one Xfce gave me before I installed Icewm, and I configured the menu file accordingly. 

Problem 1: two of the menus I placed aren't showing up (the rest are there). Did I make some error in writing the menu file code?
I thought perhaps Icewm couldn't find any of the programs I placed under "Office" and "System," so it didn't show those menus. So I tried putting the Opera menu item in those folders as well, since that was already working in the "Network" menu. But the menus still didn't show up, so I guess that wasn't it.

Problem 2: some programs aren't showing up. Like, where's Gaim? The Icewm FAQ says that icewm will ignore any programs that aren't in my PATH... but Gaim is in my PATH. Huh?

I just started using Linux a few weeks ago so I may be missing something really elementary. Any suggestions?

My menu file in ~/.icewm/menu:

> menu Accessories /home/jon/icons/tango16/applications-accessories.png {
  prog Leafpad /usr/share/pixmaps/leafpad.png leafpad
  prog Conky conky conky
}

menu Graphics /home/jon/icons/tango16/applications-graphics.png {
  prog "The GIMP" /usr/share/pixmaps/gimp.xpm gimp
}

menu Multimedia /home/jon/icons/tango16/applications-multimedia.png {
  prog Gxine /usr/share/pixmaps/gxine.png gxine
  prog GQView /usr/share/pixmaps/gqview.png gqview
}

menu Network /home/jon/icons/tango16/applications-internet.png {
  prog "Opera" /usr/share/pixmaps/opera.xpm opera
  prog Links /usr/share/pixmaps/links.xpm links
  prog Dillo /usr/share/pixmaps/dillo.xpm dillo
  prog "Mozilla Thunderbird" /usr/share/pixmaps/mozilla-thunderbird.xpm
mozilla-thunderbird
  prog Gaim /usr/share/pixmaps/gaim-menu.xpm gaim
  prog w3m /usr/share/pixmaps/w3m/xpm w3m
}

menu Office /home/jon/icons/tango16/applications-office.png {
  prog Abiword /usr/share/pixmaps/abiword.png abiword
  prog Gnumeric /usr/share/pixmaps/gnome-gnumeric.png gnumeric
  prog OpenOffice /usr/share/pixmaps
}

menu System /home/jon/icons/tango16/applications-system.png {
  prog Synaptic Package Manager /usr/share/pixmaps/synaptic.xmp synaptic
  prog Boot-up Manager /usr/share/pixmaps/bum.xpm bum
  prog Sun Java 6 Control Panel /usr/share/pixmaps/java.xpm
}

Screenshot:

---

### Post by Peter76 on 2007-06-24
Hi, nice you found my howto helpfull. I remeber having a problem like this as well, but can't remember exactly...
The only two things I notice is that in the "Office" menu, the Open-Office item is not finished properly and the same goes for the Java 6 control panel in the "System" menu. It could be that this is causing icewm not to show these menu items.

Good luck,

Peter

---

### Post by jplowman on 2007-08-02
Just in case it helps anyone - the other day I solved my problem. I read [this guy's advice]("http://www.troubleshooters.com/lpm/200209/200209.htm") about the icewm menu file. (Specifically the bit about icewm being VERY sensitive to the proper placement of spaces and tabs within its configuration files.) Then I went back to my menu file and tried to make sure all my tabs and spaces were just so.

I'm not really sure what the specific error was that kept the menu from looking how I wanted. But adjusting the spaces and tabs, with his advice in mind, fixed the problem. The menu is how I want it now. Just thought I'd share in case anyone had a similar problem.

---

### Post by kerry_s on 2007-08-03
icemc would have saved you alot of time, you just use it to open the menu file you want to modify and it handles all the complicated stuff, just remember to save before you close it. i'm simple i usually use win key+spacebar to launch most apps.
pics->

---

