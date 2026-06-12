---
title: "NTB freezes, display turns off after starting XFCE"
date: 2010-11-10
forum: Desktop Environments
---

### Post by Bheemot on 2010-11-10
I have fresh installation of Ubuntu server upgraded with apt-get dist-upgrade and with XFCE4 installed on my notebook. The problem is whenever I type startxfc, startx or X, the NTB freezes, CRT display connected to docking station/port replicator turns off, LCD in NTB gets black. The system does not respong to any signal, even the alt+sysrq ones. If I even install Xubuntu-desktop, as the X gets loaded every start, system everytime hangs after few seconds and I cannot do anything.

Now I reinstalled and tried autoconfiguration with *Xorg -configure*. If I start the X with this configuration file, the result is still the same. Log at /var/log/X11/ seems to be blank.

Any ideas? Should i try to get drivers for my video card? I thought this is not necessary, the X server should start without anything, even only with basic resolution settings. As I looked, the video card chipset (Intel 82852/82855) is detected in my /root/xorg.conf.new file.

---

### Post by Bheemot on 2010-11-15
:-k

---

