---
title: "Boot Ubuntu using NTLDR"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Ian McLeish on 2006-08-15
I an a complete Linux virgin, having tried Fedora core 3 and Mandrake before that, I always seemed to ruin my windows install. Not this time! But I have landed with one problem- I don't want to use grub to load windows.

System: Asus A7v600 athlon 3200XP
Drives 2 sata drives raid 0
2 ide drives.
I installed Ubuntu Dapper Drake onto the second / slave ide drive, and installed the grub loader onto the mbr of the master, hda. I can go into the bios and set the first boot device to be the ide master or slave, but I previously tried to put the grub loader onto hdb, and set this as the first boot device, which didn't work. With grub on hda I can set the bios to boot from the master as the first boot device, and load ubuntu. To load windows I can remove the setting in the bios and boot from the sata drives, and this will boot windows xp.

I have been trying to use a windows utility called bootpart to copy the mbr of the master drive and boot Ubuntu using the Windows NTLDR. I cannot get this to work. If I select the Ubuntu listing on booting, it just returns to the options menu again.

I assume that the grub loader is on drive hda- I can boot using that, but I tried the utility with various other options with no success. The excellent article by Philip J. Hollenbeck was my guide Thread=87751.

As I was not having any success there, I tried the dd command in ubuntu. As I say I am completely new to this OS, but I got the command dd if=/dev/hda of bootsect.lnx bs=512 count=1 typed into a terminal window, and it wouldn't allow this command. I then tried typing sudo with my root password, and that seemed to let me upgrade? though the name at the prompt remained the same. Tried that again, but it still wouldn't let me run it due to permissions.

I can manage the way the PC is, but it isn't ideal as it means a trip into the bios every OS change. I don't want to install the grub installer onto the boot (sata) drives, as my wife wouldn't have a clue how to boot windows- she just expects the power button to take her to the logon screen.

I installed Ubuntu about 10 times yesterday, and tried putting grub on hda, hdb1, hdb, and a floppy, but any way I then tried to copy the bootsector to a file (in windows) was failing. This bootpart utility shows an asterisk beside active partions, which I understand are the bootable ones. I tried copying every one in turn to a bootsect file and rebooting without success.

I did search the forums for advice, but couldn't find anything on this subject, can anyone help me? remembering I have never used Linux before. I know it can be done, but why can't I do it.

Thanks in anticipation,

Ian

Addition; I got the alternate installer iso, so would it be worthwhile trying to install the grub loader somewhere else? I did try that yesterday, but it was coming up after installation with an error 17 can't mount selected partition.

Go easy on me please, it's my first post!

---

### Post by orb9220 on 2006-08-15
Instead of all that work just make winxp the default boot Os in the grub  menu which there are many threads on, also you can change the default timeout to like 3 secs. that should please her and you from a headache.

---

### Post by Ian McLeish on 2006-08-15
Thanks Orb9220,

I really would like to do this without affecting the sata windows drives in any way, as I have had a few unbootable systems in the past, because of lilo loader, although I admit it was my mistakes rather than it's. Would prefer to keep both completely separate, as the windows install is really important for work.

Ian

---

### Post by cptnapalm on 2006-08-15
One path to explore (as I am not 100% on this) would be to install grub to the Linux partition (instead of the MBR) which should be marked as bootable in cfdisk (or whatever you use), then point the NTLOADER there.  I have a *very* vague recollection of doing that some years ago.

I *think* Linux needs a linux aware bootloader and the NT loader is (probably intentionally) braindead in that area.  So it would be loading the NT boot loader, select Ubuntu, which goes to Grub which gives you the options of kernels, select the default and off to Ubuntu land.

Again, this is something which is might be a method; it is not a known working solution.

---

### Post by Indras on 2006-08-15
The proper command should be:
```

sudo dd if=/dev/hda of=bootsect.lnx bs=512 count=1

```

Assuming grub was properly installed to the MBR of /dev/hda, this should output a file, called bootsect.lnx, which is 512 bytes in size, and contains your master boot record.  Now just move this file into your C:\ of Windows, and edit the boot.ini file to point to it (here's an example):

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\bootsect.lnx="Ubuntu Linux 6.06"

```

Oh, and keep in mind that since you made the bootsect.lnx file as sudo, it will be owned by root, so you'll need to either chown that file to belong to you, or move it with another sudo command (or gksudo nautilus).  If all else fails, just put it on a floppy disk and reboot to windows to put the file to your C drive.

Now, you just have to boot back into Windows and use the fixboot and fixmbr commands to reset your master boot record to all zeroes (factory default).  Then, your computer will simply boot from the first bootable partition.  Installing grub (or lilo) to the mbr overwrites this "normal" behavior.

If you don't have the fixboot and fixmbr commands (Win 9x/Me and NT 3.5-4.0 I believe don't have them) then just get an old Windows 98 boot floppy and boot to DOS.  From the C:, type:
```
FDISK /MBR
```

Now, as long as your master boot record is empty and your Windows drive is set to bootable (has the star by the partition in fdisk), and your BIOS is configured correctly, it should boot NTLDR.  From there, you'll probably have to hit F8 to bring up the menu and manually select Ubuntu.  But, that's probably best if you want this to be a transparent boot process to Windows for your wife.

If Ubuntu fails to boot, you may have to reinstall grub to the first sector of your linux partition.  This is not the same as the master boot record, mind you.

To do this, boot from the Ubuntu CD, find out the partition number that contains your /boot folder (you may have a separate partition for it, but it will most likely just reside with your root partition).  From command line type:```
sudo grub-install /dev/hdax
```
Where x is the partition number that contains your /boot folder.  Then, restart.

---

### Post by Sasquatch2000 on 2006-08-15
I had some similar boot questions:

[Dual Boot with SATA and IDE, Need Help!!](http://www.ubuntuforums.org/showthread.php?t=46003)

[boot multiple OS's](http://www.ubuntuforums.org/showthread.php?t=204049)

---

### Post by kiwi_bloke on 2006-08-15
Hi Ian
I know the problem - I too had to feel my way into a similar problem (W98 + XP + Ubuntu). Anyway I wondered if these points might help:

Assuming you installed Ubuntu after windows, the Ubuntu installer will automatically set up Grub with a menu to choose between Windows and Ubuntu. As has already been stated, this saves you a lot of time and grief because it makes the whole thing easy to set up.

My wife too wanted Windows to appear just by switching on. You can do this by editing the file called menu.lst You'll find in the folder /boot/grub. Open the file and read it thru. You'll find you can set the default boot OS (in your case and mine windows) _and_ you can set a small delay of your choice (the countdown is displayed and can be stopped by pressing a key) before windows boots to give you time to select Ubuntu. 
Later you can even arrange a splashscreen of your choice to appear but that'S a different topic.

IMPORTANT. Make backups before you alter files.

---

### Post by BillZog on 2007-01-04
Very much a noob here and have been hittin the threads, assorted other refs, herman's site, etc., etc.. Read several things that may or may not be true, but three things for certain: installation of Ubuntu for dual boot ain't easy; installation for boot involving two or more HDD's harder still; and SATA drives make it even more difficult.

 In my case, the MBR is on my old SATA drive and my working XP program is on the new SATA drive (without the NTLDR and boot.ini files. Right now BIOS will boot to either my old corrupted XP or new clean install of XP and all is well. What happens is that on booting the BIOS refers to NTDR and boot.ini on my old drive and boots either the new XP or old XP. But, I am darned glad I haven't tried to install Ubunty yet and will not until I am a lot more certain that I have got it right. What would have happened to me if I had tried to install with the regular install disk in the free space on my old drive is that Grub would have overwritten the boot loader on the old (system) drive and I would have lost access to either version of XP. That may be where you are right now and I am goin to follow closely how you work your way out of that. You can probably fix the MBR, hope so.

Two threads that show a lot of promise to me are:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

[http://www.ubuntuforums.org/showthread.php?t=236846](http://www.ubuntuforums.org/showthread.php?t=236846)

The second shows how another guy finally resolved the issue, the first a revised grub that seems to help the way along.

What I am going to try when I have studied enough is: 1. use Partman to set up the partition on the old drive where I want to put Ubuntu; 2. install via the alternate Ubuntu CD (that's supposed to give a tad more control); and 3. see if supergrub has special use. Somehow, for me, I think the answer is going to be in booting to Ubuntu via NTLDR.

Good luck.

BZ: Still confused but learning slowly, I hope.

---

