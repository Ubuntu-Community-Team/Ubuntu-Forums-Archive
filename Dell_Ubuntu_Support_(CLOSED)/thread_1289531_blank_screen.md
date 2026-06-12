---
title: "blank screen"
date: 2009-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jonbo123 on 2009-10-12
My mini dell computer uses ubuntu and when I turn it on the screen is black except for the lettere MBR 2FA, Also the keyboeard does not work. Can you help me ? About all I have been able to do is take out the battery and replace it but it did nothing.

---

### Post by jonbo123 on 2009-10-12
> **jonbo123 said:**
> My mini dell computer uses ubuntu and when I turn it on the screen is black except for the lettere MBR 2FA, Also the keyboeard does not work. Can you help me ? About all I have been able to do is take out the battery and replace it but it did nothing.
my mini dell computer uses Ubuntu and when I turn it on, the screen is black except for the letters MBR 2FA. I also can not use the key board. I have taken out the battery and put it back in to no avail. Can you help me?

---

### Post by QIII on 2009-10-12
Does this happen immediately at power on, before you get the Dell splash?

Edit:

Just found this, if you are running a Mini9:

**Booting into Recovery mode**

 If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command. 
You can enter the recovery mode following these steps: 

[LIST=1]
[*]Boot the mini 9 while pressing ESC every second
[*]When you see the "MBR 2FA:"  prompt or similar, the boot process is stopped.
[*]Press ENTER and ESC very fast one after the other.
[*]You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode.
[/LIST]

Taken from:  [https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

If you are able to get in, then someone should be able to help you with setting your delay to something more reasonable.

---

### Post by jonbo123 on 2009-10-12
> **QIII said:**
> Does this happen immediately at power on, before you get the Dell splash?
 The Dell splash comes on very briefly.

---

### Post by jonbo123 on 2009-10-12
Okay, I'll give it a try and let you know, thank-you.

---

### Post by jonbo123 on 2009-10-12
As of now the only thing I can get up is the Boot Menu which consists of : hard drive;CD/DVD/CD-RW;Removable Devices;Network Boot;
Diagnostics then below it says <enter setup>

---

### Post by jonbo123 on 2009-10-12
I have tried all of them to no avail

---

### Post by lukjad on 2009-10-12
Can you boot into a the Ubuntu Live CD and check if you can see any partitions?

---

### Post by jonbo123 on 2009-10-12
No, I don't have Ubuntu CD. I did just get up the set up utility though. As you can tell I am a novice at this, I don't know which to select. Advanced;security;boot. If you think I should stop and wait for someone to help me just let me know.

---

### Post by lukjad on 2009-10-12
> **jonbo123 said:**
> No, I don't have Ubuntu CD. I did just get up the set up utility though. As you can tell I am a novice at this, I don't know which to select. Advanced;security;boot. If you think I should stop and wait for someone to help me just let me know.
How come you don't have an Ubuntu Live CD? Didn't you have to have it to install Ubuntu?

---

### Post by QIII on 2009-10-12
> **lukjad007 said:**
> How come you don't have an Ubuntu Live CD? Didn't you have to have it to install Ubuntu?

Dell's machines can come preinstalled.  The OP may have gotten it that way.

Darn computer makers selling computers without disks!

---

### Post by lukjad on 2009-10-13
> **QIII said:**
> Dell's machines can come preinstalled.  The OP may have gotten it that way.

Darn computer makers selling computers without disks!
Really? I'm shocked. I would have thought they would at least have sent a copy of the disk...

---

