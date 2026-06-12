---
title: "Dual boot vista with ubuntu + mediadirect + restore files"
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by a_tom on 2007-06-09
I have dell E1505 with windows vista installed, I want to dual boot it with Ubuntu while keeping mediadirect and most importantly the restoration capability. my restore files are on a separate partition which I am not going to touch, I'll chop off my vista partition into  two and then install Ubuntu. problem is when installing Ubuntu the grub boot loader will mess up the MBR, so neither mediadirect nor restore files will work. I am thinking of installing Ubuntu without the grub boot loader and then figure out a way to configure the vista boot loader to boot Ubuntu. have anyone tried this before or is it workable. also I am afraid  the MBR is messed up by  just repartitioning the vista drive. I appreciate it if anyone know how to get around this.

---

### Post by jiminycricket on 2007-06-10
I don't believe you can boot Ubuntu from the Vista bootloader.  You can boot Ubuntu from the windows xp bootloader (which would be the trouble in your case-- no win xp) though, which can then chainload to the Vista bootloader.  I'm not 100% sure what MediaDirect is, but I wonder if GRUB could chainload and boot into it like it can boot into XP.

---

### Post by envoy on 2007-06-16
I used the information on this page:
[http://linux6400.wordpress.com/2007/04/06/installing-ubuntu-edgy-eft-610/]("http://linux6400.wordpress.com/2007/04/06/installing-ubuntu-edgy-eft-610/")
which worked for me (w/ Feisty).
I did experience some issues with hibernation / sleeping in Ubuntu though, so be careful there.

Edit: so this recipe will have you boot Ubuntu from the Vista boot menu and the MediaDirect key will still work.

---

