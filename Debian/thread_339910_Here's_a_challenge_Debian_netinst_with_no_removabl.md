---
title: "Here's a challenge: Debian netinst with no removable media (Except 1 floppy)"
date: 2007-01-16
forum: Debian
---

### Post by happy-and-lost on 2007-01-16
I have here a crippled old computer, running XP very slowly. I want it Linuxed, but the CD drive does not work, I tried replacing it with a new drive, but the BIOS does not register it, so it's unuseable. I want to do a Debian netinst, but the only removable media I have available is a single floppy disk. I don't want to lose the existing WinXP install, as there is now literally no way of reinstalling it, and without a CD drive I can't install my copy of PartMag. 8. This machine has no ethernet port, and is connected to a router by USB (The firmware is *nix based, I think, I know most Linuxes recognise it and use it without need for special installation).

So is it possible? (If not, would it be possible to boot from my xubuntu.iso on my hdd using only one floppy, I'm not fussy!)?)

:twisted:

---

### Post by neowolf on 2007-01-16
[http://www.debian.org/releases/stable/i386/ch04s03.html.en](http://www.debian.org/releases/stable/i386/ch04s03.html.en)

---

### Post by happy-and-lost on 2007-01-16
Sadly that requires 4 floppies, I only have one at my disposal.

---

### Post by mips on 2007-01-16
Never mind.

---

### Post by happy-and-lost on 2007-01-16
I'm part way through fixing my CD problem. I realised I had the drive jumper set to secondary on a master channel... *d'oh* Having changed that, it's not showing up in Windows (but it is in bios), ergo I cannot burn my isos :(

---

### Post by mips on 2007-01-17
If you have another PC you can also boot the pc over the network if it supports that. So no disks/cds required at all.

---

### Post by flangemonkey on 2008-04-08
reformat the disk in between loading, it takes about 1 minute.

It's how I did it.

---

