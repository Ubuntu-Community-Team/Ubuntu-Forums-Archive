---
title: "GRUB fails on IBM thinkpad t60 running 7.04"
date: 2008-02-04
forum: Desktop Environments
---

### Post by glopv2 on 2008-02-04
I've had ubuntu installed successfully for a few months. However, recently, when I put ubuntu to sleep the computer hung while trying to go into sleep. I held down the power button to reset the computer, but now immediately after the BIOS, the screen just prints "GRUB " and nothing else. Nothing else happens, and the computer is clearly stuck.

Why would this happen seemingly randomly like this? It had been working for months beforehand.

Please help!

---

### Post by logos34 on 2008-02-05
I'd try doing a filesystem check/repair first

boot up the ubuntu live cd and run

**sudo fsck /dev/hda1** (replace hda1 with your root partition)

---

