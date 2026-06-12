---
title: "full format in ubuntu"
date: 2004-12-15
forum: Desktop Environments
---

### Post by darkwithstars on 2004-12-15
what is the command for doing a full format that clears both my hard drive and my mbr?

---

### Post by adbak on 2004-12-15
I don't know the command, but you could always pop the Ubuntu cd back in.

---

### Post by az on 2004-12-15
Open up a console and type this:
man parted

and then type this:
man mke2fs

---

### Post by darkwithstars on 2004-12-15
does anyone know the command for doing a full format including the mbr in ubuntu? thanks. i tried what the above poster said but all i got were manuals which i couldn't understand.

---

### Post by jdong on 2004-12-15
You **MUST** boot from a Linux livecd to perform these steps.


At a root LiveCD console, type **dd if=/dev/zero of=/dev/hda**.

WARNING: **THIS WILL COMPLETELY ZERO YOUR HARD DRIVE**! That means that the data won't be recoverable in any do-it-yourself manner! PROCEED WITH CARE.

---

### Post by darkwithstars on 2004-12-15
will it clear my mbr as well?

---

### Post by jdong on 2004-12-15
yep.

---

### Post by jdong on 2004-12-15
You don't need to let it finish.... Once it wipes for 1-2 seconds, it's well past the MBR and the partition table -- at which point this drive will appear to be blank / brand-new to the OS.

---

### Post by mrosenlof on 2004-12-15
[QUOTE=jdong]You don't need to let it finish.... Once it wipes for 1-2 seconds, it's well past the MBR and the partition table -- at which point this drive will appear to be blank / brand-new to the OS.[/QUOTE]

True, but a sophisticated snooper could still find things on the drive.  If your goal here is to prevent such snooping, let the 'dd' finish.  If your goal is to clear it enough to put it to another use, you can kill it early.

---

### Post by VanBoy4881 on 2007-05-15
> **darkwithstars said:**
> does anyone know the command for doing a full format including the mbr in ubuntu? thanks. i tried what the above poster said but all i got were manuals which i couldn't understand.


[generator generator Ebay generator Mortgages](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

