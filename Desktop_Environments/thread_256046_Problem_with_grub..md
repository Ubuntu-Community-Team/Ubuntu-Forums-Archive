---
title: "Problem with grub."
date: 2006-09-12
forum: Desktop Environments
---

### Post by Najand on 2006-09-12
I usually use different grub bootsplashes and I make new ones, once a while. Yesterday I was looking at the forum ans I saw this thread  [Howto : GfxBoot ( Grub like suse )]("http://ubuntuforums.org/showthread.php?t=208855")

I looked at screenshots and I thought they are nice so I tried to install them on my dapper machine at university.

I  did  the procedure as following:

   i. I installed grub-gfxboot.deb and the message.ubugrey
  ii. I removed grub
 iii. I installed grub-gfxboot.deb
  iv. Then copied the message.ubugrey to /boot/grub
   v. backed up the menu.lst file
  vi. Added "gfxmenu /boot/grub/message.ubugray" to top of menu.lst file
 vii. Executed "sudo grub"
viii. In grub, "grub> find /boot/grub/stage1" found two devices. Two devices are hd(0,1) and hd(0,2). I have two different Linux systems on my system, so hd(0,2) belongs to the other system's grub, which is not used now.
  xi. I did both "root hd(0,1)" and then "setup hd(0)"
   x. I then "quit" the grub command and reboot the computer manually from terminal.

However,

when it rebooted, there were no sign of any splash, just the old grub menu (White Characters on Black Background) I tried to install it over and over but  got the same result all the time. Did I made a mistake during installation? If so I would appreciate it if someone can teach it to me.
Thank you very much in advance.

---

### Post by Najand on 2006-09-12
Anyone? Please help.

---

