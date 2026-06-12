---
title: "Complete move from Windows."
date: 2005-06-19
forum: Desktop Environments
---

### Post by ASPX9100 on 2005-06-19
Hi, 
I am not the type of person who wants to have more than one operating system on my computer.  So, I want to switch from Windows to ubuntu.  I have a few questions. 
1.  How can I play protected WMAs?
2.  I need replacement software, to operate as the following:
a.  Rollercoaster Designer/3D simulator
b.  Lexmark Z715 printer monitor.

Also, can you help me out with my drivers
ATI 9200SE
Realtek AC97' audio
Integrated Intel LAN


Thank you for all of your help, the switch is hopefully going to be very successful, fun, and exciting.  I may have some more questions down the road.

Sincerely, 
ASPX9100

---

### Post by ASPX9100 on 2005-06-19
Anyone?

---

### Post by Moobert on 2005-06-19
Realtek AC97' audio

Ubuntu supports this by default (mine ran fine out of the box :)

ATI 9200SE

just a matter of getting the now gui installer of the ati site for linux.

as for protected WMAs and a Rollercoaster Designer.

wine runs windows media player and RollerCoaster Tycoon fine... though there are probably some gnu solutions about :)

---

### Post by ASPX9100 on 2005-06-19
[QUOTE=Moobert]Realtek AC97' audio

Ubuntu supports this by default (mine ran fine out of the box :)

ATI 9200SE

just a matter of getting the now gui installer of the ati site for linux.

as for protected WMAs and a Rollercoaster Designer.

wine runs windows media player and RollerCoaster Tycoon fine... though there are probably some gnu solutions about :)[/QUOTE]

Oh, really, Rollercoaster Tycoon 3, yes!  Thanks for your reply.  Would you mind helping me set up wine, and RCT3.    \\:D/

---

### Post by Chousuke on 2005-06-19
I wouldn't recommend getting the ATI drivers for the 9200. As far as I know, the free 3D accelerated drivers ('radeon' in xorg configuration) work with that card, and are of higher quality. (Won't break with X/kernel upgrades either)

---

### Post by ASPX9100 on 2005-06-19
[QUOTE=Chousuke]I wouldn't recommend getting the ATI drivers for the 9200. As far as I know, the free 3D accelerated drivers ('radeon' in xorg configuration) work with that card, and are of higher quality. (Won't break with X/kernel upgrades either)[/QUOTE]
I'll see into it.  Unless the default 3D free drivers give me troubble, I see no reason to get the ATI ones.

---

### Post by Moobert on 2005-06-19
[QUOTE=ASPX9100]Oh, really, Rollercoaster Tycoon 3, yes!  Thanks for your reply.  Would you mind helping me set up wine, and RCT3.    \\:D/[/QUOTE]

[http://digital-conquest.ath.cx/wiki/index.php/Roller_Coaster_Tycoon_3](http://digital-conquest.ath.cx/wiki/index.php/Roller_Coaster_Tycoon_3)

I think your need the non-free verson of wine 'cedega' for 3, but 1 and 2 should play in wine.

get either wine or cedega installed (apt-get install wine or buying cedega)

then type:

wine <appinstallername>.exe
or 
cedega <appinstallername>.exe


also you will need hardware 3d support working before any of this.

---

### Post by ASPX9100 on 2005-06-19
I think I'm gonna use something called scream machines, how well does that run in WINE?

---

### Post by Moobert on 2005-06-19
[http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php)

lists of apps running in wine

[http://digital-conquest.ath.cx/wiki/index.php/Category:Games](http://digital-conquest.ath.cx/wiki/index.php/Category:Games)

lists of apps running in cedega

---

### Post by veraction on 2005-06-19
Well, I also have a computer with a ATI Radeon 9200 which is causing me major problems with Ubuntu 5.04 (Hoary). However, I think I will try replacing "ati" with "radeon" in that xorg config file.
[B]
Is that all I have to do? Or do I need to download something first?[/B]

---

### Post by ASPX9100 on 2005-06-19
Well, I had problems with SuSE.  If ubuntu gives me problems, I'll either use, Fedora 4, Gentoo, or Slackware.

---

