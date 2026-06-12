---
title: "Unable to boot into Ubuntu after removing storage drive"
date: 2006-09-20
forum: Desktop Environments
---

### Post by frequenicity on 2006-09-20
I had a storage drive connected internally through a IDE bus that was named "/dev/hde1". I had this drive configured to mount automatically as a read only drive (ntfs drive). However, I took the drive out and am instead using it as an external drive now. My problem is this:

Now, when booting Ubuntu, I get stuck at "waiting for root file system to load" and it hangs there and after a few minutes goes to shell with a message (approx):
ALERT - Unable to find /dev/hde1 (or does not exist) entering shell mode.

So does anyone know (aside from installing the drive again) how to get past this from the shell/live cd?

---

### Post by darkpark on 2006-09-20
next time you get to that error and it drops you into the command line, simply type "exit" and press enter.  once (if) your system is up and running.  modify your fstab (located in /etc) so that drive is no longer listed.  either delete the line or put a comment in front of it.

---

### Post by frequenicity on 2006-09-21
Only problem there is that typing exit still gives me the same error.

Is there a way to edit the fstab from the shell or live cd? Knoppix perhaps?

---

### Post by Ramses de Norre on 2006-09-21
That's absolutely possible, mount the drive from the live cd and edit the file ;)

---

### Post by frequenicity on 2006-09-22
I am still getting hung up on "waiting for root filesystem...." and then eventually errors saying ALERT! Can not locate HDE1 and kicks me to the shell. 
-I know this is because I removed an IDE bus that would load before my boot hard drives (causing my boot drives to change from hde* to hda*)
-Using Knoppix I have editted my fstab for the changes.
-I still get the same error. (though my fstab says nothing about hde1)

So what other scripts load at startup that tell Ubuntu which drives to look for? I really don't want to put everything back the way it was (I removed it because I no longer need 3 IDE channels for HDDs and now have a TV tuner card) 

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/proc            /proc           proc    defaults        0       0 
/sys             /sys           sysfs    noauto          0        0
/dev     /hda1       /               ext3    defaults,errors=remount-ro 0       0
/dev    /hda5       none            swap    sw              0       0 
/dev     /hdc        /media/cdrom0   auto    user,noauto     0       0
/dev     /fd0   /media/fd0  auto   user,noauto,exec,umask=000    0 0

---

