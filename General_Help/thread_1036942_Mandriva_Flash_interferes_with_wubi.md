---
title: "Mandriva Flash interferes with wubi"
date: 2009-01-11
forum: General Help
---

### Post by mheller on 2009-01-11
I "successfully" installed with wubi 8.10 for dual boot with Windows Vista for x64. However, when I try to boot ubuntu, grub starts, I see the Mandriva Flash splash screen, and the ubuntu boot fails. I can get into the console, but I don't know what to do to remedy the problem.

Ideally I would still want to be able to boot from the Mandriva Flash usb drive.

Any suggestions?

---

### Post by mheller on 2009-01-11
I solved my own problem. There were a couple of mbr files and a lst file in the C: root directory left over from the Mandriva utility to install a Flash boot item. When I put those in the Windows recycling bin I was able to reboot and complete the wubi installation successfully.

This post is from Ubuntu. :p

---

