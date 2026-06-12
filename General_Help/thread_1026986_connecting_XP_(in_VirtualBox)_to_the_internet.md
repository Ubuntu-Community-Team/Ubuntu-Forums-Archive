---
title: "connecting XP (in VirtualBox) to the internet"
date: 2008-12-31
forum: General Help
---

### Post by happinesskills on 2008-12-31
I have windows XP installed inside VirtualBox & I can not find a way to get it to connect to the internet. I have 3 mobile broadband (E160G modem) & I use Gnome PPP to get that to connect. I am able to install the drivers & software for it in XP because it shows up as a CD drive (which it did in windows before I got rid of it). But after I install the driver software, it doesn't detect the modem.

any help is appreciated

---

### Post by pytheas22 on 2008-12-31
VirtualBox emulates a virtual network interface for Windows XP to use, so installing drivers in the virtual machine for your device won't do anything.

As long as Ubuntu has Internet access, however, it should automatically be bridged to your Windows virtual machine as long as you enable NAT networking in the VirtualBox settings (this should be the default).  Is it enabled?

---

### Post by happinesskills on 2008-12-31
I've enabled it now. I'll just check after I've finished downlaoding a program

---

### Post by happinesskills on 2008-12-31
It's working now. Thanks for the help, & such a quick reply. Thanks

---

