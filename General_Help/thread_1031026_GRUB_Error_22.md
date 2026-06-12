---
title: "GRUB Error 22"
date: 2009-01-04
forum: General Help
---

### Post by CLUGENHEIM on 2009-01-04
Hey.. well, I know why I have this error, and I know how to fix it.

The problem is my disc drive... it stops working sometimes. And right now is one of those times. This means I can't boot the Windows Repair Disc.

What can I do now?

edit: oh, and I can't boot from USB, and I tried using my external disc drive that I have for when my internal one goes out and it doesn't work either; probably because it uses USB.

---

### Post by Tim Sharitt on 2009-01-04
If you do have a usb drive to boot from, check the bios setup to make sure it is ahead of the hard drive in the boot order.

---

### Post by CLUGENHEIM on 2009-01-04
> **Tim Sharitt said:**
> If you do have a usb drive to boot from, check the bios setup to make sure it is ahead of the hard drive in the boot order.

My laptop doesn't have the option to boot from USB at all.

---

### Post by CLUGENHEIM on 2009-01-05
Uhh, need a fix if there is one, my computer is useless right now...

---

### Post by logos34 on 2009-01-05
need more info...you have windows dual boot?  XP? Which release of ubuntu?

Have a floppy drive?

---

### Post by CLUGENHEIM on 2009-01-05
> **logos34 said:**
> need more info...you have windows dual boot?  XP? Which release of ubuntu?

Have a floppy drive?

Yes, dualboot with XP.

Ubuntu 8.10.

No floppy drive, but oddly enough an option to boot from one in the bios..

---

### Post by CLUGENHEIM on 2009-01-05
I've been playing with my BIOS and apparently I can boot from a network server.. could I use this to fix GRUB somehow?

edit: I'm going to try this: [http://bergcube.net/post/2007/01/08/Ubuntu-laptop-struggle](http://bergcube.net/post/2007/01/08/Ubuntu-laptop-struggle)

---

### Post by CLUGENHEIM on 2009-01-05
Bump again, I NEED this fixed. :(

---

### Post by logos34 on 2009-01-05
try making a [SmartBootManager floppy]("https://help.ubuntu.com/community/SmartBootManager")--it might help you to boot from the cd drive (unless it's a hardware failure in the drive itself).  If you can do that, you can boot a live cd to fix the grub error/reinstall grub

not sure about the method/link you posted

---

### Post by CLUGENHEIM on 2009-01-05
> **logos34 said:**
> try making a [SmartBootManager floppy]("https://help.ubuntu.com/community/SmartBootManager")--it might help you to boot from the cd drive (unless it's a hardware failure in the drive itself).  If you can do that, you can boot a live cd to fix the grub error/reinstall grub

not sure about the method/link you posted

I have no floppy drive on the laptop. =/

And I think the lens is dirty or something on the drive. It will sound like it is tying to read the disc (no Boot CDs work at all btw, I've tried several and I know for a fact it is the drive) then it will make a "failing" sound that I can't describe really..

---

### Post by logos34 on 2009-01-05
> **CLUGENHEIM said:**
> I have no floppy drive on the laptop. =/

And I think the lens is dirty or something on the drive. It will sound like it is tying to read the disc (no Boot CDs work at all btw, I've tried several and I know for a fact it is the drive) then it will make a "failing" sound that I can't describe really..

duh. sorry.  (how did I misread that) hey it's a monday--takes me a while to get up to speed for the week

yeah, you could try isopropyl alcohol and a q-tip.  wish I had another suggestion

---

### Post by CLUGENHEIM on 2009-01-05
> **logos34 said:**
> duh. sorry.  (how did I misread that) hey it's a monday--takes me a while to get up to speed for the week

yeah, you could try isopropyl alcohol and a q-tip.  wish I had another suggestion

Haha.. 

Yeah, I'll try cleaning the lens. Hope like hell that it works because I can't find any (easy) guides to PXE booting. x_x

---

### Post by CLUGENHEIM on 2009-01-06
*sigh* problem still exists. Help?

---

