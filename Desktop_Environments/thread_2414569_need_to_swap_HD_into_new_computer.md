---
title: "need to swap HD into new computer"
date: 2019-03-12
forum: Desktop Environments
---

### Post by Autodave on 2019-03-12
Purchased a new video card and installed it.  Video card was bad and shorted out motherboard. So, probably going to buy new computer.  Currently I have 18.04 running on an SSD with Win10 on a spinner HD.  How can I either transplant the SSD with 18.04 on it, or what do I need to copy from that drive to a fresh install to keep all of my games, passwords, etc.  All pics, tunes and already copied to other locations: not worried about them.

---

### Post by oldfred on 2019-03-12
If new computer it will be UEFI.
Is older computer have UEFI or BIOS boot type installs. Or more correctly is it MBR(msdos) or gpt? 
If UEFI/gpt, you probably can just plug in SSD and have it work. If different video card/chip you may have to recovery mode boot to change video driver.

I generally prefer new installs and restore from backup. Becomes a good way to confirm you backup procedures fully include everything you need to restore system.
All your user settings are in /home. If you made some system settings changes those would be in /etc. I edit grub and copy those edits back into /home so my backup of /home includes those settings. But /etc is not large so easy to copy if desired. But new system may need some default settings that are different, so best not to just restore /etc anyway, but just copy settings changes you made to system back, if needed.
I export list of installed applications to make it easy to restore them.
If you have server apps or perhaps some games may install in folders in / (root). Your backup needs to then include those also.

       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636) 

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by Autodave on 2019-03-12
So, if I start with trying to just plug it in and powering up the PC, will I have to update grub?  If so, how?

---

### Post by oldfred on 2019-03-12
It will probably work.
If old BIOS/MBR configuration, you must have UEFI Secure boot off to be able to boot in BIOS mode.
If video card/chip different you may need nomodeset and if different wireless chip you may need then to install new driver. Or possibly boot in recovery mode to install driver. Best to initially boot with hard wired Internet.

---

