---
title: "What can I do to make GNOME 3 run?"
date: 2012-01-05
forum: Desktop Environments
---

### Post by flyingfisch on 2012-01-05
GNOME 3 is extremely slow for me. My hardware specs are:

RAM: 512MB
Graphics: nVidia GeForce 5200
Processor: 2Ghz

I have the 173 nVidia drivers installed. What should I do/upgrade to make GNOME shell work?

---

### Post by 3Miro on 2012-01-05
Is this a laptop? You need the proprietary Nvidia drivers, however, if this is a laptop, then you have Nvidia Optimus and that is really bad news.

If this is a desktop, then going to Additional Drivers and installing the Nvidia proprietary driver should do the trick.

---

### Post by ubiquitin.jf on 2012-01-05
Whilst there are no official minimum system requirements published for gnome-shell, I suspect that it is not intended to run on a system with 512MB RAM. I suggest you try XFCE or LXDE instead.

---

### Post by flyingfisch on 2012-01-05
I am using XFCE right now. Should I upgrade my RAM, then?

---

### Post by ubiquitin.jf on 2012-01-05
That would be the best course of action if you really would prefer Gnome 3 to XFCE.

---

### Post by hhh on 2012-01-05
The Fedora Project website is stating that 768MBs of RAM are needed to run gnome-shell, with 1G recommended for best performance...
[http://fedoraproject.org/en/get-fedora](http://fedoraproject.org/en/get-fedora)

Also, I run gnome-shell 3.2 (from Debian unstable) on 1G RAM with a low-end Nvidia card (6150LE) and the animations are slightly choppy, I'd expect that to be the same with your card even if you do increase your RAM.

---

