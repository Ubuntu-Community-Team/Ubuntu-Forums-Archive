---
title: "GRUB error 17"
date: 2005-12-26
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-26
I was using Windows and changed the size of my Linux partition with Powerquest Partition Magic. Now, when I turn my computer on, I get the message:
"Loading Grub...
Error 17"

Do I have to reinstall Linux or there is a way of solving this problem without reinstalling Linux?

---

### Post by blair on 2005-12-26
According to this page:

[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)

this means: Cannot mount selected partition. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. Be sure to check your root(x,y) settings in your grub.conf. 

You should be able to fix this by renitializing GRUB. I'm no GRUB expert and can't provide explicit instructions, but if you search the forum (or linuxquestions.org) for GRUB you will likely find a thread with instructions you can use.

---

### Post by ubuntuubuntu on 2005-12-26
Can someone explain me how to fix GRUB configuration?

---

### Post by ubuntuubuntu on 2005-12-26
My windows partition has a lot of free space. Can someone tell me how I can boot in Windows, in order to copy some files from my linux partition to my windows one and then reinstall linux? Is there a way to create a diskete and then boot windows?

---

### Post by Irony on 2005-12-26
**Restoring XP Bootloader**

*Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*

or

**Restoring Grub Bootloader**

Get a partition list;

*sudo fdisk -l*

Boot from the install ubuntu CD and at the prompt typed;

*boot: rescue*

Go to a  mount point, determined from paritition list;

dev/disc/disc0/part?

At the sh-3.00# prompt type;

*grub-install /dev/hda*

After being returned to the prompt, do;

[I]#umount /dev/hda?
#reboot[/I]

Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot will work.

---

### Post by ubuntuubuntu on 2005-12-26
I'm sorry, but I can't understand. Could you explain it in detail?
> **Irony]

**Restoring Grub Bootloader**

Get a partition list said:**
> #umount /dev/hda?
#reboot[/I]

Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot will work.


Thank you.

---

### Post by Griff on 2005-12-27
[QUOTE=Irony]**Restoring XP Bootloader**

*Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*
[/QUOTE]
Woo!  Did a search and found your post.  fixmbr did the trick! :p

---

### Post by cvmostert on 2005-12-30
> **Irony]**Restoring XP Bootloader**

*Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*

or

**Restoring Grub Bootloader**

Get a partition list said:**
> #umount /dev/hda?
#reboot[/I]

Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot will work.


worked like a charm! thank you SO much...
this was my problem after taking out my secondary hdd, on which i also had ubuntu installed... ta

---

