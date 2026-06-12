---
title: "splash screen"
date: 2011-04-11
forum: Desktop Environments
---

### Post by shortfuse69 on 2011-04-11
why is so damm hard to change the splash screen in ubuntu 10.10? like what's up with that anyways? I've tried like 10 different solutions and not a single one works, I really need this to finish my thin client, it really important that I be able to change the splash screen

---

### Post by Krytarik on 2011-04-11
Please see these earlier posts:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)
[http://ubuntuforums.org/showthread.php?p=10561873#post10561873]("http://ubuntuforums.org/showthread.php?p=10561367#post10561367")

Greetings.

---

### Post by shortfuse69 on 2011-04-11
I have tried all of those and nothing seem to work, I have even tried plymouth manager and nothing seems to work I have read all most ever guide to doing it.

---

### Post by Cpierce on 2011-04-11
Have you tried grub customizer ?  It worked for me. 

[http://ubuntuforums.org/showthread.php?t=1665875](http://ubuntuforums.org/showthread.php?t=1665875)

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Make sure the image is in .png extension

---

### Post by Copper Bezel on 2011-04-12
And don't forget the crucial update-initramfs -u step that actually commits your changes to the boot process (or breaks your install, on older versions at least.) = ) But seriously, what part of the process doesn't work? Are you having trouble installing the screens, trouble selecting them, or just no result on boot?

Cpierce: That's for the grub menu. I *think* the "splash screen" being referred to here is the Plymouth boot progress screen.

---

### Post by shortfuse69 on 2011-04-12
yeah I'm talking about the plymouth boot screen

---

