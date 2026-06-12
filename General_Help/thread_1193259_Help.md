---
title: "Help"
date: 2009-06-21
forum: General Help
---

### Post by likol on 2009-06-21
i m currently using windows xp pro on my toshiba satellite a300 laptop

 i downloaded the iso for 9.04 ubuntu

BUT I CANT MAKE MY LAPTOP BOOT FROM IT

i burned the iso but it just DOESNT BOOT

it boots fine from the windows cd i made i just cant understand wtf is wrong with ubuntu and why it doesnt boot

any help?

---

### Post by likol on 2009-06-21
also i installed 8.04 version but i cant get internet with it, there is no internet......

thats why i need 9.04 but it doesnt boot

---

### Post by 3rdalbum on 2009-06-21
You need to help us to help you. Does the computer just completely ignore the disc when booting up? Does it start booting Ubuntu from the disc and then stop at some point, and if so exactly when?

If it gets to the menu on the disc where you can choose to try Ubuntu, install it directly, check the disc etc, have you tried specifying safe boot options? (you can find out what options are available by pressing one of the F keys listed at the bottom of the screen).

If the disc won't even start to boot up (as though it wasn't even in the drive), how exactly did you burn it? Did you use the special disc image burning feature of your burning software? Did you burn at a low enough speed like 8x?

---

### Post by likol on 2009-06-21
i used nero 9 burning rom

when i boot from cd 

it shows up a black page with something written on it

Yukon PXE v6....

(c) Copyright ...

Client Mac Address ...

GUID ...

DHCP

then after DHCP it goes like .........................................................................

i dont know what to do im desperate, i wasted 4 cd's for this

---

### Post by master_kernel on 2009-06-21
Check that your BIOS options are set to boot CD-ROM first. If this doesn't work, make a USB version of Ubuntu and try booting from that.

EDIT: You should be able to find a boot menu. When the BIOS screen comes up, try to enter it (usually somewhere between F8 and F12) and select the CD drive.

---

### Post by likol on 2009-06-21
thanks 

i ll try using unetbootin, hope it works

---

### Post by Gen2ly on 2009-06-21
Nero is a good burning program but perhaps the iso is corrupt or nero is having problems burning disk images properly.  Did you get the iso from the official repositories?:

[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

Perhaps you can try to burn as suggested in the Ubuntu wiki:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by 3rdalbum on 2009-06-21
Yukon PXE is a feature on your motherboard that allows the system to boot from a network drive. Turn it off in your BIOS, or put it after the CD-ROM and hard disk in the boot priority. Having said that, it's probably appearing because the CD is not in a readable format - i.e, you may have burned it incorrectly.

Did you use the special disc image burning feature of your burning software? Did you burn at a low enough speed like 8x?

Some computer magazine coverdiscs have a copy of the latest Ubuntu, already bootable from their CD. You might want to give that a try.

---

