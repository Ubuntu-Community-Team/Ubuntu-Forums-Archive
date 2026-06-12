---
title: "Interesting BIOS question"
date: 2006-07-29
forum: Desktop Environments
---

### Post by AngryMallard on 2006-07-29
OK So I think this is a pretty interesting situation... I just bought an E-machines desktop (pentium 4, 1.3 gHz) secondhand that initially came pre-loaded with Windows ME. I am trying to install Ubuntu on it now but I can't get to the bios menu for some reason. I just put a brand new 200 gb hard drive in it, but the computer will only boot to the hard drive (which is why I would need to get to the bios, to change the boot order). Is there perhaps some way to get some kind of version of the install CD image to the hard drive so the computer will boot to it and install the OS?

---

### Post by stevea1210 on 2006-07-29
Why can't you get into the bios?  
Is it password protected and you don't know the password?  
     If that's the case, remove the cmos battery for a few seconds, and the password is cleared.

Do you not know the key to initiate bios setup?
     Common ones are esc, del, F1, F2, or F10

Are you using a usb keyboard?
     You may need to use a ps2 keyboard on some older pc's to be able to get into the bios setup.

---

### Post by AngryMallard on 2006-07-29
I've tried all of the function keys and none work and I do know the password so that's not a problem either.

---

### Post by patrickthebold on 2006-07-30
Try finding out your motherboard and googleing that.

---

### Post by jgcamp99 on 2006-07-30
Yes, Go to emachines and determine the model you have, find out what key combination gets you into the bios, so that you may change it. Otherwise you'd have to download their flash utility and appropriate bios file to reflash it and it would be like starting over again with the same bios revision or you may even have a newer version of it to use.

---

### Post by cantormath on 2006-07-30
> **AngryMallard said:**
> OK So I think this is a pretty interesting situation... I just bought an E-machines desktop (pentium 4, 1.3 gHz) secondhand that initially came pre-loaded with Windows ME. I am trying to install Ubuntu on it now but I can't get to the bios menu for some reason. I just put a brand new 200 gb hard drive in it, but the computer will only boot to the hard drive (which is why I would need to get to the bios, to change the boot order). Is there perhaps some way to get some kind of version of the install CD image to the hard drive so the computer will boot to it and install the OS?

sometimes its two keys.....like a function key and del.

did you just try del? maybe alt+del?

good luck.

---

### Post by tturrisi on 2006-07-30
Do you have a usb keyboard?  If so, try using a regular keyboard to enter the bios & once there locate an option to "enable legacy support" which allows usb keyboards & mice to be detected and used before an os loads.  Emachines usually use the del key for bios.  Most keyboards have 2 del keys. try the del key that's grouped with the number pad.  (I had an old emachines that would only accept that del key)

---

### Post by tommcd on 2006-07-30
On my Emachines T1840 computer (about 4 yrs old) I hit DEL to get into BIOS. Also, on my Emachines, the boot order is fixed like this and cannot be changed:
1st boot: CDROM
2nd boot: hard drive
3rd boot: floppy
In other words, if it is like mine, it is already set to boot from the CDROM. Try placing the ubuntu disc in the CDROM and see if it boots to it. There is not much in my Emachines BIOS that can be changed anyway. Most of the stuff is fixed. Good luck!

---

