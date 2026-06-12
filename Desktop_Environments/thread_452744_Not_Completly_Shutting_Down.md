---
title: "Not Completly Shutting Down"
date: 2007-05-23
forum: Desktop Environments
---

### Post by simoneale on 2007-05-23
I'm new to all this Linux 'Terminal' Stuff... so I need quite a lot of help (I'll be in here Lots)...

Anyhew..

I recently installed Ubuntu 7.04FF, Dual Booting with XP Home (for the Wife!!), and I've noticed that when I shut down from Linux Both My Logitec USB Mouse and 3COM Router stay connected (The Blue LED on the Mouse and the LAN LED stay Lit).

This doesn't happen when Closing down Windows!?!... 

Its as if Linux isn't shutting down properly/Completely!... 

I've read somewhere that it might be an ACPI thing, but I don't know how to check/amend this (the Terminal Command etc...).

Help Me Please!?!?!?!?... :(

_My Spec is:_ AMD64 3400+ (Skt 754), Abit NF-v8 Motherboard (with the latest BIOS), 512mb PC3200, Elsa gForce MX440 64Mb DDR, Maxtor 200Gb with XP Home SP2, Quantum 20Gb with Ubuntu v7.04FF... etc...

---

### Post by angryfirelord on 2007-05-23
Ok, open up gnome-terminal, type **sudo gedit /boot/grub/menu.lst**. On the kernel line, add this:

acpi=off apm=power_off

An example would be this:
```

## ## End Default Options ##

title Debian GNU/Linux, kernel 2.6.18-3-k7
root (hd0,1)
kernel /boot/vmlinuz-2.6.18-3-k7 root=/dev/hda2 ro **acpi=off apm=power_off**
initrd /boot/initrd.img-2.6.18-3-k7
```
[http://ubuntuforums.org/showthread.php?t=359190&highlight=Incomplete+shutdown+issue]("http://ubuntuforums.org/showthread.php?t=359190&highlight=Incomplete+shutdown+issue")

When you're done, click save and see if that fixes it.

---

### Post by simoneale on 2007-05-24
> **angryfirelord said:**
> Ok, open up gnome-terminal, type **sudo gedit /boot/grub/menu.lst**. On the kernel line, add this:

acpi=off apm=power_off

An example would be this:
```

## ## End Default Options ##

title Debian GNU/Linux, kernel 2.6.18-3-k7
root (hd0,1)
kernel /boot/vmlinuz-2.6.18-3-k7 root=/dev/hda2 ro **acpi=off apm=power_off**
initrd /boot/initrd.img-2.6.18-3-k7
```
[http://ubuntuforums.org/showthread.php?t=359190&highlight=Incomplete+shutdown+issue]("http://ubuntuforums.org/showthread.php?t=359190&highlight=Incomplete+shutdown+issue")

When you're done, click save and see if that fixes it.

Not Doing That again!?!?!... I just had to manually edit me Grub back to its default!... This Command stopped Ubuntu from Booting!... it got to 3 blocks on the Progress Bar and Hung!!... :(

---

### Post by angryfirelord on 2007-05-24
Ok, try one or the other. It's probably the apm line that's screwing it up, but I can't be too sure.

---

