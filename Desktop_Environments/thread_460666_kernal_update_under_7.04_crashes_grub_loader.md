---
title: "kernal update under 7.04 crashes grub loader"
date: 2007-05-31
forum: Desktop Environments
---

### Post by groged on 2007-05-31
Upgrade kernal crash

I selected an automatic kernal update for 386 (7.04). In the morning my system was hung at the grub loader. I have tried the "rescue" option from the install CD. The rescue install crashes with the error---"not syncing: VFS unable to mount root fs on unknown block(104.1)

I'm a realativly new user of ubuntu though have been using computers for a long time and am not afraid of command line.


Please help me get my system back running! My guess is that I have some sort of corrupted boot block where the grub loader is supposed to be. By the way, I have a seperate /boot partition of 4 gigs along with a /root partition.

Thanks in advance!!

---

### Post by iamhugeinjapan on 2007-06-01
Can you boot up by selecting an older kernel in the Grub menu?

---

### Post by groged on 2007-06-01
Nope, my system is hung with caplock an scroll lock lights blinking.  I have to do a hard reboot.  I tried every key combination I could think of to try to get to a command line.

Thanks a bunch for the response!!  I am getting worried no one had any idea's or wanted to help me.  I have two years of family photo's and video I transfered to this drive/system.  I'm worried about losing it!



---

### Post by merlinus on 2007-06-01
Restart your computer, and press e at the grub menu.  That will enable you to change the grub location.

For example, in my case the update changed grub root to (hd0,6).  Setting it back to (hd0,7) solved the problem.  Then I edited /boot/grub/menu.lst to make the change permanent.

Good luck!

-merlin

---

### Post by groged on 2007-06-01
Thanks a bunch!!  I'm back into ubuntu and am able to back up my photos and family video (As promised to my wife).

The fast help has really sold me on ubuntu!  It reminds me of the old days running my Amiga 3000 as my primary machine.  The level of support to fellow uses was high in the Amiga world like this one.

---

