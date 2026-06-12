---
title: "USB HDD Problem"
date: 2008-05-03
forum: Desktop Environments
---

### Post by m0e on 2008-05-03
I am having a problem accessing USB hard drives since upgrading to Hardy. After the upgrade plugging in a USB hard drive resulted in various problems - the background turns white, all my icons in the Gnome panel turn into white squares with a red x on them that are mostly unresponsive, the mouse will still control the cursor but if a mouse click can get any response I seem to get an error message I can't read because all of the fonts are squares. I can use hotkeys to get out of x but I don't seem to be able to do anything from the command line. The TTY hotkeys give me a login but after entering a username and pressing enter the keyboard stops responding and nothing happens. Checking the log files in /var have given me no clues because there are no entries after the USB hard drive is recognized. USB flash drives work fine, the problem seems to be only with hard drives. I have four USB drives, a 120gb drive formatted as FAT32, a 160gb formatted as Ext3 (this is my Hardy boot drive, the internal drives are a pair of 60gb drives in a RAID0 configuration formatted as NTFS for my Windows partition), a 250gb drive formatted as FAT32, and a 320gb drive formatted as NTFS. 
I went into the gconf settings and turned off automount in the Nautilus preferences and now I can manually mount the 120gb drive through Nautilus, but if I try to mount the 250gb drive that way I still get the same problems, and the 320gb still tries to automount and screws everything up the same as before. All the hard drives work fine when booting from the Windows XP partition on this computer or booting the computer from the Gutsy live CD, Hardy live CD, Gparted live CD or any of my other computers (Windows Vista, Windows XP, Windows 2000, Ubuntu Feisty, or my other Ubuntu Hardy install, but I haven't tried them on any of my Macs). I have checked the drives using the various disk repair utilities in the different OS's of my machines and not found any errors. I ran a couple of virus scans on the drives and found no problems there also. I can access the internal RAID partition through dmraid and ntfs3g so I don't think thats the problem. 
Both my Hardy machines were upgraded through the Update Manager system, not a fresh install. I would rather not do a fresh install on this machine because of the hassle with setting up the MBR's after the install. Ultimately I would like to move the Hardy partition to the internal drives but there isn't enough free space on the RIAD partition and I haven't had any luck making a disk image of it to restore  the Windows partition after upgrading the internal drives. The 120gb drive and the 250gb drives were accessible when I had Feisty installed on this machine, but I didn't have the 320gb drive then so I don't know if it would have. I did a fresh install when upgrading to Gutsy but was only running that for a couple of weeks before doing the Hardy upgrade and didn't use any of the USB hard drives during that time.
If anyone has any suggestions as where else to look for problems or if I need to provide any more info just let me know.

---

### Post by acelin on 2008-05-03
I know that WD and Seagate Drives have supposedley poor support for Linux in general, but I dont think that is the problem. It seems as if your upgrade wasnt succesful. The servers were so taxed that many people didnt get all of the updates, leaving them with some problems. Try updating again jsut to make sure you got everything, and if that doesnt work, you might want to search more on what is up with your USB ports.

---

### Post by m0e on 2008-07-26
Well I'm back with this problem again. About a week after my first post in this thread the problem seemed to go away after an aptitude dist-upgrade. But I tried plugging in one of my USB hard drives today (first time in a couple of weeks) and the problem is back. Anyone else having this problem? I found this [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666358") in the archives and this seems like the same problem I'm having (my dmesg ends the same as the original post in that thread), but I have let my my machine run for over a half an hour after plugging in the USB drive without the desktop restoring itself. Anyone have any other thoughts or suggestions?
I am a little disappointed with Hardy at this point. Of the four machines I currently have running Ubuntu the two I upgraded to Hardy are the least stable. My other Hardy machine randomly crashes for no consistent reason, it can run for days without a problem and then the desktop will freeze (stop responding except the mouse will still move the cursor, but I get no response from the mouse buttons or keyboard) maybe four-five times in an hour. Or I might have to reboot every couple of minutes until i get tired of it and just choose a different OS from Grub. Doesn't seem to matter what I am doing, this has happened browsing files, listening to music, browsing the internet, watching movies, even with only one open window. But both of these machines have no problems running Windows XP, openSuse, Fedora or any of the Linux Live CD's I have so I don't think its hardware related. Not a very good example for a LTS release.

---

### Post by m0e on 2008-07-28
Okay, as I had said before I am booting Hardy from an external USB hard drive, when the drive is unplugged during power-up this computer boots into Windows but if the USB drive is plugged in during power-up it reads the MBR from the external hard drive and boots into Ubuntu. So I was messing around (I am not computer literate enough to call it anything more than that) today, it seems to me that when I plug in another USB drive while running Ubuntu the system seems to get confused as to which drive the OS is on. After connecting the second external drive the few icons on the desktop that respond at all give me an error message about “file not found” so I am wondering if the OS is trying to find the files on the newly inserted hard drive instead of the boot drive. Is this possible? And if it is what can I do to fix it?

---

### Post by m0e on 2008-07-31
Well I don't know which one did it but apparently one of the 42 updates I installed through aptitude today seems to have fixed my issue again. Hopefully this time it will stick. Thanks for all who helped.

---

