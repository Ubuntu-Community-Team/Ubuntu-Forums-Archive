---
title: "Trying to dual boot and Windows XP disc doesn't recognize hd on 1525n"
date: 2009-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Unikraken on 2009-07-18
I'm really sorry ahead of time for asking a semi-windows related question on an Ubuntu forum but this is the best Dell Inspiron forum I've been able to find.

I've got the 1525n and I'm trying to dual boot with XP Home, but when I run the install disc (inserting the disc and restarting and letting it auto-boot) I can't get anywhere with the installation because the XP disc doesn't realize there is a hard drive in the computer. Is anyone else having this sort of issue?

Again, I'm sorry and embarrassed to have to ask an Ubuntu forum this question but I'm not seeing anything about this anywhere else.

---

### Post by balaknair on 2009-07-18
Most newer PCs and laptops have AHCI enabled for SATA drives, and requires SATA drivers, which XP lacks- it can only use the IDE mode, and so it fails to detect your hard drive.

**Option 1:**

Go into the BIOS settings at start up and change the BIOS settings for the hard drives. The actual wording varies between different makes, but what you need is turn AHCI off(it may also be labelled SATA mode or Enhanced mode) and enable IDE(may also be labelled compatibility mode). Booting from the XP CD should now work fine.

Note: After installation, you can install the SATA drivers for XP and re-enable SATA mode in the BIOS. This doesn't work for all Motherboards though(I've been able to get XP working with SATA mode with some chipsets, but not with others). With most Intel desktop boards I've tried this on XP refuses to boot up in SATA mode, whereas Via chipsets seem to work just fine.

**Option 2:**

Slipstream the XP SATA drivers if you can get them from the manufacturers website, either using a Floppy drive(press F6 during installation), or by creating a slipstreamed XP boot CD using nLite.
Easy to follow guide given here
[http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/](http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/)

You can also slipstream other hardware drivers,service packs and security updates in to the CD while you're at it.

---

