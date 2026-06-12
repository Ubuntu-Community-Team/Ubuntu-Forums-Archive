---
title: "Weird Boot Sequence"
date: 2009-03-06
forum: General Help
---

### Post by twistedsum on 2009-03-06
I just installed Ubuntu lastnight with dual boot with WinXP.  There are several options to choose from at bootup (eg. Ubuntu, WinXP).  When I choose WinXP it then asks me to choose between Ubuntu and WinXP.  How do I resolve this.  What I want is when I bootup, I just want to choose between Ubuntu and WinXP, and when I choose WinXP I want it to boot up WinXP and not give me a choice between Ubuntu or WinXP.

Thanks!

---

### Post by pothik on 2009-03-06
> **twistedsum said:**
> I just installed Ubuntu lastnight with dual boot with WinXP.  There are several options to choose from at bootup (eg. Ubuntu, WinXP).  When I choose WinXP it then asks me to choose between Ubuntu and WinXP.  How do I resolve this.  What I want is when I bootup, I just want to choose between Ubuntu and WinXP, and when I choose WinXP I want it to boot up WinXP and not give me a choice between Ubuntu or WinXP.

Thanks!
Once you choose XP/Ubuntu it sould boot that OS..if you had multiple windows befaore Ubuntu installation then choosing Windows may led to winboot loader... else asking two times is wired!  if you are using grub bootloader then you have to edit /etc/grub.conf for any change .. paste your grub.conf here.

---

### Post by kanikilu on 2009-03-06
Can you post the contents of your /boot/grub/menu.lst file? It probably couldn't hurt to also post the output of "sudo fdisk -l".

Was this a "vanilla" ubuntu install, or Wubi or something like that?

---

### Post by twistedsum on 2009-03-06
I figured it out.  I had to edit the boot.ini, I removed the following command:

c: \wubildr.mbr="ununtu"

:D

---

