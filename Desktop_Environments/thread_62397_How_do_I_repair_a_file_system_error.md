---
title: "How do I repair a file system error?"
date: 2005-09-04
forum: Desktop Environments
---

### Post by troether on 2005-09-04
I'm a new user of Hoary 5.04. I got it installed and configured with out too much trouble. I have it set up as a duel boot with windows on the primary drive and ubuntu on its own 4G hard drive. I really appreciate having an alternative to windows and find the Gnome desktop pretty easy to use. However, I think I may have made a mistake when I deleted a html file from the desktop and then restored it to different folder than it was associated with.  I opened it in my browser (firefox) but then it froze up and I was forced to reboot. During the boot these are the messages I get:
     Checking root file system . . .
     Contains file system with errors - check force
     /:Inode 65649 (/home/thomas/Unofficial Ubuntu5.04 Starter                         
     Guide_files/style.css)  has a bad mode (0177644)
     /:UNEXPECTED INCONSISTENCY; Run fsck manually
     *(i.e., without -a or -p options)    [fail]
     *fsck failed. Please repair manually and reboot. Please note that the   
     *root file system is currently mounted read-only.
     * To remount it read-write:
            #mount -n -o remount,rw /
     Control-D will exit from this shell and reboot the system
     bash: dircolors : command not found.
     #

I tried  the fsck.ext2 command with the -p option but I get an error message about not recognizing the device. I'm  really unclear about how to proceed- like which options to use or even how to denote the device. Do I need to remount the root to read-write first? Should I use the -b option or what?  I'm hoping there is a simple solution. Any explicit directions on how to manually repair the file system would be greatly appreciated.
Thanks.

---

### Post by essexman on 2005-09-04
> **troether]I'm a new user of Hoary 5.04. I got it installed and configured with out too much trouble. I have it set up as a duel boot with windows on the primary drive and ubuntu on its own 4G hard drive. I really appreciate having an alternative to windows and find the Gnome desktop pretty easy to use. However, I think I may have made a mistake when I deleted a html file from the desktop and then restored it to different folder than it was associated with.  I opened it in my browser (firefox) but then it froze up and I was forced to reboot. During the boot these are the messages I get:
     Checking root file system . . .
     Contains file system with errors - check force
     /:Inode 65649 (/home/thomas/Unofficial Ubuntu5.04 Starter                         
     Guide_files/style.css)  has a bad mode (0177644)
     /:UNEXPECTED INCONSISTENCY said:**
> 
     *fsck failed. Please repair manually and reboot. Please note that the   
     *root file system is currently mounted read-only.
     * To remount it read-write:
            #mount -n -o remount,rw /
     Control-D will exit from this shell and reboot the system
     bash: dircolors : command not found.
     #

I tried  the fsck.ext2 command with the -p option but I get an error message about not recognizing the device. I'm  really unclear about how to proceed- like which options to use or even how to denote the device. Do I need to remount the root to read-write first? Should I use the -b option or what?  I'm hoping there is a simple solution. Any explicit directions on how to manually repair the file system would be greatly appreciated.
Thanks.


Have you tried what the warning suggests?  ```
mount -n -o remount,rw /
``` and then run e2fschk {device} without -a or -p. Your decive is probably something like /dev/hdb1 (after / is mounted).

Have you installed using ext3?

---

### Post by troether on 2005-09-04
Dear essexman 
Thanks for your suggestion on how to fix my problem.
I tried the remount,rw / command and that was successful but then when I ran the e2fsck /dev/hdd1 (I finally figured out my device name) I got a big WARNING!  DANGER, file system is mounted and this command could cause EXTREME damage to file system. - continue Y/N?  So I chickened out and said no.  Then I decided to reboot and skip the remount,rw / command and went with just the e2fsck /dev/hdd1 command and it walked me through the repair and a succesful conclusion.  Thought you would like to know.

---

### Post by essexman on 2005-09-05
[QUOTE=troether]Dear essexman 
Thanks for your suggestion on how to fix my problem.
I tried the remount,rw / command and that was successful but then when I ran the e2fsck /dev/hdd1 (I finally figured out my device name) I got a big WARNING!  DANGER, file system is mounted and this command could cause EXTREME damage to file system. - continue Y/N?  So I chickened out and said no.  Then I decided to reboot and skip the remount,rw / command and went with just the e2fsck /dev/hdd1 command and it walked me through the repair and a succesful conclusion.  Thought you would like to know.[/QUOTE]

troether, this is great news.  Hard drive identification is difficult in Linux. I think it might help if new users were advised to make notes during installation.

I am surprised this happened though. If you are using ext3 filesystem I would have thought this should have fixed itself.

Glad all is well

---

### Post by dangman4ever on 2005-09-11
[QUOTE=essexman]Have you tried what the warning suggests?  ```
mount -n -o remount,rw /
``` and then run e2fschk {device} without -a or -p. Your decive is probably something like /dev/hdb1 (after / is mounted).

Have you installed using ext3?[/QUOTE]

How do u run e2fschk?

I''ve only used Ubuntu for about three weeks now and I ran into the same problem as troether.

---

### Post by dangman4ever on 2005-09-11
This should be stickied somewhere. Or at least placed in the Guide.

I've had this problem 3 times now and only now was I able to find the answer.

---

