---
title: "No gxmame and grustibus?"
date: 2005-03-01
forum: Gaming &amp; Leisure
---

### Post by Alessio on 2005-03-01
I have installed xmame-x but there isnt' any gui for it! Not grustibus and gxmame, where can i find it?

---

### Post by MedusaErodeus on 2005-03-01
Be sure to get the Debian pkgs.....

[http://gxmame.sourceforge.net/downloads.php](http://gxmame.sourceforge.net/downloads.php)

Good Luck

---

### Post by Alessio on 2005-03-01
[QUOTE=MedusaErodeus]Be sure to get the Debian pkgs.....

[http://gxmame.sourceforge.net/downloads.php](http://gxmame.sourceforge.net/downloads.php)

Good Luck[/QUOTE]
 Only debian packges? Not ubuntu packages?

---

### Post by Dullin on 2005-03-02
[QUOTE=Alessio]Only debian packges? Not ubuntu packages?[/QUOTE]
 If applications started doing packages for every based distro there is there wouldn't be much time left to code the app itself. Just be happy that there is a .deb and use it (or even better, learn how to compile and install stuff).

---

### Post by leech on 2005-03-03
Actually, the .deb from gxmame.sourceforge.net is ancient (from Dec, 2003) so you'll want to add 'deb  [http://anarxia.dyndns.org/debian/](http://anarxia.dyndns.org/debian/) ./' to either Synaptic or your /etc/apt/sources.list file and then install gxmame through apt-get.  

As a side note, the version of xmame in Ubuntu's repositories are quite old as well, xmame 0.92 is out, you can add 'deb [http://www.bootsplash.de/files/debian/](http://www.bootsplash.de/files/debian/) unstable main' and you'll get that version.  You'll probably want the xmame-sdl version, as it supports going full screen better (at least in my experience).  Though it seems that joystick support is broken.  (I'm not sure if it's gxmame's fault, or the xmame packages that are on bootsplash's website.)  Unfortunately, they are the only ones I've found that has the 0.92, Debian has 0.90 and Ubuntu currently has 0.86.

Leech

---

### Post by Sniffer on 2005-03-29
Thks for the update...

Men i'm becoming old ;-)

---

