---
title: "Removing GRUB"
date: 2009-06-12
forum: General Help
---

### Post by Ripplinger on 2009-06-12
I don't want to delete either WinXP or Linux, but I just want GRUB gone.  I've tried every way I could find googling so far and GRUB still remains on the system.  

My set up and boot order is:
1TB drive C: Drive with WinXP, normal boot up drive always
1TB drive D: which is a clone of C:
120GB drive with Ubuntu on it

I can boot into the 2 WinXP drives by manually selecting them, and but nothing will auto boot with the GRUB menu there.

When I first installed Ubuntu I unplugged the 2-1TB drives so there was no confusion and I didn't accidentally screw up a good drive.  I decided to reinstall just Ubuntu though after adding other packages I wanted to get rid of, and probably just unplugged the C: Drive and that's when GRUB came onto the system.  I just want to boot up into the C: Drive always without having to select anything from a menu, and then select either the D: Drive or the Linux drive manually at boot up.  

The first problem with GRUB if I let it boot without me selecting the drive is that it stopped with an Error 17.  After trying everything unsuccessfully that I could find to fix and get rid of GRUB, I decided to just try reinstalling Ubuntu, clicked on the Advanced button and made sure the boot menu option was unchecked, and now I still have GRUB but it stops at Error 15 instead.  I then tried Super Grub at boot up and now I'm back to Error 17 with GRUB still there.  When I use the Classic method described [here,]("http://www.supergrubdisk.org/wiki/UninstallGRUB") it stops halfway though and then beeps constantly until I reset the computer.
  
Right now I can boot into C: Drive with WinXP by manually selecting the drive using F8 at bootup.   When I try to boot into D: Drive doing the same, I get GRUB Loading stage1.5, Error 17.  When I try to boot into the Linux Drive doing the same manually, I get stopped at Error 15.  I can only access the Linux Drive with the LiveCD.

I really don't care about the GRUB errors, even if fixed, I don't want the extra GRUB menu ever.   Can anyone give me a sure way to get rid of GRUB so I can boot into all 3 drives again?

Thanks for any help.  Definitely liking Linux enough to not give up on this.

---

### Post by LepeKaname on 2009-06-12
You can set the "timeout" variable to 0 (in /boot/grub/menu.lst) so it will not be displayed. I personally recommend to have grub installed because if something fails in a kernel upgrade (or distibuition update), you can still enter to your linux partition with previous kernel versions. 

For example, last week I disabled accidentally "dbus" service from start-up, so during the boot process I could only use my keyboard for a short period of time (not enough to fix the problem). In this case having grub was very helpful. And so on...

---

### Post by Ripplinger on 2009-06-12
Since it's popping up either Error 15 or 17 and stops loading there, that really won't help.  Unless I'm misunderstanding and that eliminates it from the mix altogether?  

Edit:  I'm really a newbie to Linux btw, so probably would need specific instructions for much more than that.  I was in the menu.lst file earlier today trying things so that one thing I am familiar with.

---

### Post by LepeKaname on 2009-06-29
Sorry for my late response. 

Try reinstalling grub... did you tried already? Once you have a working grub, you can follow my suggestion:

edit /boot/grub/menu.lst and set timeout=0 or timeout=1. And thats all.

---

