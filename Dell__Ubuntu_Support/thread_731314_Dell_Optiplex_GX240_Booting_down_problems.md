---
title: "Dell Optiplex GX240 Booting down problems"
date: 2008-03-21
forum: Dell  Ubuntu Support
---

### Post by tymiller48 on 2008-03-21
I have a Dell Optiplex GX240  Pentium 4  Speed:v1.80GHz,  512MB PC133 SDRAM s, IDE 20GB hard drive, CD-ROM 16X CD-RW,  AGP Video Card, 10/100 3COM integrated network... I have Installed Ubuntu 7.10 and Xubuntu 7.10  several times they install fine, and run fine, surfing the web no problem, but when I shut down I get theses errors, and PC does not shut off.

NetworkManager: <Warn> nm_signal_handler () : Caught signal 15, shutting down normally   
NetworkManager:  some numeric errors 
NetworkManager: Deactivating device eth0  :confused:

---

### Post by peterthewolf on 2008-05-20
Replace network manager with wicd (just search wicd in google).

Add acpi=force to the kernel line in /boot/grub/menu.lst

---

