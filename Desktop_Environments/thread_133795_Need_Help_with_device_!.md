---
title: "Need Help with device !"
date: 2006-02-20
forum: Desktop Environments
---

### Post by xXx 0wn3d xXx on 2006-02-20
I've been trying to get my psp to work but then my internet went out for 5 hours :) I plug it in and I can't get it to come up unless I go under Administration > Disks and then it shows up. The problem is that I can't put anything on it because it's owner is the root. Even when I go to my script folder and use the root on it doesn't work :( What can I do to make it so that my user has the permission to use the device and put things on it ???

---

### Post by xXx 0wn3d xXx on 2006-02-20
how can I change the permissions ?

---

### Post by xXx 0wn3d xXx on 2006-02-20
???

---

### Post by xXx 0wn3d xXx on 2006-02-20
help me please

---

### Post by RAOF on 2006-02-20
You just want to mount your psp as a removable drive, yes?  So presumably it's not being automounted by gnome-volume-manager.

I'm not familiar with how the psp works as portable storage, but I'll assume that it's formatted like a FAT disc.  In this case, the (dodgy, but easy) way to do it is to plug in the psp, go to a terminal, and type "dmesg".  Some of the last output of that command should be about your psp, and it'll include such information as which device it is named as.  Something like /dev/sda1

Once you've identified this, you can run "sudo mkdir /media/psp" (you only need to do this once), then "sudo mount -t vfat -o rw,umask=0000 /dev/sda1 /media/psp".  This should load the contents of the psp into the /media/psp directory, and you should be able to read/write to it.

The more correct, difficult way to do this would involve writing a udev rule ([http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)) to make sure the psp is always identified as /dev/psp or similar, then adding a line in your fstab to mount it from /dev/psp.  I'd **definitely** check that the dodgy way works first :)

---

### Post by xXx 0wn3d xXx on 2006-02-20
Thanks for replying, I'll try it in the morning.

---

### Post by xXx 0wn3d xXx on 2006-02-21
ok I got it to mount but I need root permissions for the device. How can I change the permission from root to all ? I also don't have gnome volume manager under sessions b/c I thought it was for sound x_x so I disabled it. Can someone tell me the name it needs to be and the order of it ?

---

### Post by xXx 0wn3d xXx on 2006-02-21
sigh........should I just re-install and do the default installation ? Please tell me what you think b/c it will take 2 hours to re-install it....

---

### Post by RAOF on 2006-02-21
Load up gnome-volume-manager (before you plug in your PSP)!  That's the Gnome program that handles automounting of removable storage - plug it in, and it should **just work**(tm).  It doesn't need to have any particular order - just add "gnome-volume-manager" anywhere in your session.

To fix the "root permissions" problem, you'll always need root privs to mount the device (unless you add a line to your fstab, which unless you do the udev rules thing will not always work).  The "-o umask=0000" thing should allow everyone to read/write to the psp.  Try running "sudo chmod 777 /media/psp", see if that helps.

---

