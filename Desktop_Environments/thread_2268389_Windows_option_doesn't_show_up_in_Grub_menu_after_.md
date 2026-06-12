---
title: "Windows option doesn't show up in Grub menu after boot repair"
date: 2015-03-08
forum: Desktop Environments
---

### Post by deepakgarg on 2015-03-08
I used Boot Repair many times but I still don't see the Windows option in my Grup menu. Here's the paste from Boot Repair; [http://paste.ubuntu.com/10560476/](http://paste.ubuntu.com/10560476/)
The paste clearly shows that there's a menuentry for windows but in reality it doesn't show up when I boot my laptop. I also looked into 'Advanced Options' but to no avail. I have two Ubuntu operating systems and 1 Windows system in my laptop. When I tried "Recover MBR" in the boot repair disk, it simply reinstalled Windows as the default OS and hence whenever I booted my laptop, Windows would load without any menu options. Can someone please suggest how can I fix my Grup so that it shows Ubuntu and Windows operating systems in the menu.

---

### Post by yancek on 2015-03-08
The boot repair script at the very top indicates Grub installed to the mbr of sda pointing to the core.img file on sda5 and that it exists.  sda5 contains Kali Linux and if you look at the grub.cfg file for sda5, there is no entry for windows.  However, on sda8 where you have Ubuntu installed, there are windows entries.  If you can boot Ubuntu, do that and just run:  sudo grub-install /dev/sda  and you will then be using the Grub bootloader from Ubuntu.

---

### Post by deepakgarg on 2015-03-08
Thanks a ton. It worked like a charm. The paste link I had posted was an old one but I could understand your sugesstion.

---

