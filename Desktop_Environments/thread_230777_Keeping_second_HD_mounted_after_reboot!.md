---
title: "Keeping second HD mounted after reboot!"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Irwin J. Finster on 2006-08-06
Hi,

I just installed Xubuntu on an old Athlon 700 machine and it runs like a charm, very very pleased with it. :) 

Now I have a second HD in this PC wich I want to mount as a folder in my home folder for keeping backups and some other data. I can successfully mount the disk using the System/Disks dialog, but when I reboot the system the disk is no longer mounted :-| 

Is there a way to make the mounting premanent?

Thanks,

Irwin

---

### Post by ertai on 2006-08-06
you'll have to edit fstab yourself.

- just open a terminal and type in 'sudo gedit /etc/fstab'
- He'll ask for your password.
- And then look for the place where you're 2nd harddisk should be mounted. In that rule stands also a 'noauto'. Just delete that word and the ',' before it.
- The it schould be fixed.

Be carefull with what you change. If you change to much or the wrong thing you can brake your install.

---

### Post by cantormath on 2006-08-06
> **Irwin J. Finster said:**
> Hi,

I just installed Xubuntu on an old Athlon 700 machine and it runs like a charm, very very pleased with it. :) 

Now I have a second HD in this PC wich I want to mount as a folder in my home folder for keeping backups and some other data. I can successfully mount the disk using the System/Disks dialog, but when I reboot the system the disk is no longer mounted :-| 

Is there a way to make the mounting premanent?

Thanks,

Irwin

Here is an in depth tutorial on how to install a 2nd hard drive.
[http://yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)

This is similar, but simpler in someways.
[http://personal.riverusers.com/~thegrendel/lnxpg3.html](http://personal.riverusers.com/~thegrendel/lnxpg3.html)

Here is an indepth howto on moving your /home to a different partition or drive.
[http://www.ubuntuforums.org/showthread.php?t=46866](http://www.ubuntuforums.org/showthread.php?t=46866)

This is similar, and possibly simpler to follow.
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

hope it helps.

---

### Post by Irwin J. Finster on 2006-08-06
Worked like a charm thanks to both of you! :mrgreen:

---

