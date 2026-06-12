---
title: "[SOLVED] Dell m1530 Eject button not working"
date: 2008-03-11
forum: Dell  Ubuntu Support
---

### Post by havanahjoe on 2008-03-11
I haven't seen anyone have this issue anywhere so I'm posting here to try and get some help.

The eject button on my m1530 does not work under Ubuntu 7.10 Gutsy.  All the other buttons work fine, I got them working with Amarok.  I can eject by assigning another shortcut key without a problem, but when I go to Keyboard Shortcuts under Preferences and try to assign the eject button to the eject function, the button only blinks and it is not registered by the configuration manager.

It glows/blinks about 16 times and then turns off and nothing ever happens.

Does everyone else have their eject button working on their XPS laptops?  I assume the key function is called xf86audioeject, but I can't edit the setting manually through "Keyboard Shortcuts" because it always capture the key combination.

Does anyone know what configuration file can be edited to change this manually?

---

### Post by havanahjoe on 2008-03-19
I just re-installed Ubuntu root due to my root partition getting corrupted.  I still am unable to use the eject button when in X, but it works if I use the button while booting up or while in the BIOS or in Vista of course.

No one experiences this on their m1530??

---

### Post by forceofnature on 2008-03-19
I have the m1330 and it does the same thing.  I have had it eject using the button before but I think the problem is that it is not getting the instruction to unmount the drive.  I just right click on the drive and then click eject which works.  There must be some way to reprogram the key to eject a disk properly.

---

### Post by havanahjoe on 2008-03-20
Actually you are correct.  If I umount /mnt/cdrom and then press the eject button it works.  I guess we need a script that needs to issue the umount command and then eject the cd.

---

### Post by havanahjoe on 2008-03-20
If you run lshal -m on a terminal you can monitor the HAL messages that are generated.  All the media keys except the eject button generate an event.  I guess the eject button is directly wired to the DVD drive so it can't umount and then eject and will only eject if the drive is not mounted.

---

### Post by havanahjoe on 2008-03-20
Well, found a solution for the problem.

Since Linux locks the drive when a CD is mounted, the hardwired Eject button will not work unless we get rid of this lock.  I found this thread that explains how to do it:

[http://ubuntuforums.org//showthread.php?t=115499](http://ubuntuforums.org//showthread.php?t=115499)

Once you run that command, the OS won't lock the cdrom anymore and you will be able to eject the CD or DVD with the eject button ANYTIME.  This will also generate a warning from Gnome about unsafe device removal.

Maybe in future versions this will be fixed.  It seems that some drives don't report this properly, so maybe future versions will support our DVD drive better and will allow ejecting without this patch.

For now, anyone wanting to eject their media without assigning a key combination to Gnome (I had assigned Ctrl + E for example) can follow the example above to get a work around.

---

