---
title: "menu.lst"
date: 2006-01-04
forum: General Help
---

### Post by mlookn on 2006-01-04
here is a copy of my grub/menu.lst what do I need to change to get my xp to boot so can get rid of the autochk problem
thankyou.
menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by DoorGunner on 2006-01-04
add this 

Title Windows           
root (hd0,2)     
chainloader +1


it will depend on here your root for windows is actually located. (hd0,2). remember grub always subtracts one number from the actual location. ie in this case hda += hd0 in grub and ,2 is the third partition in.

chainloader +1 is the boot instruction for windows

---

### Post by mlookn on 2006-01-04
[QUOTE=DoorGunner]add this 

Title Windows           
root (hd0,2)     
chainloader +1


it will depend on here your root for windows is actually located. (hd0,2). remember grub always subtracts one number from the actual location. ie in this case hda += hd0 in grub and ,2 is the third partition in.

chainloader +1 is the boot instruction for windows[/QUOTE]

doorgunner   where do I go to change it can I do that in terminal i'm new at this.

---

### Post by canadianwriterman on 2006-01-04
Actually, are you asking what you need to change to have Windows XP as the default boot system? If so, you don't need to add anything, just change as shown here in bold:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default 5**

Your default wait time before the system automatically boots into the default is currently set at 10 seconds. You can reduce that somewhat, but be careful not to make it too short. If you make it 0 or 1 second, then you won't have time to change the boot to Ubuntu when you want to.

---

### Post by mlookn on 2006-01-04
[QUOTE=canadianwriterman]Actually, are you asking what you need to change to have Windows XP as the default boot system? If so, you don't need to add anything, just change as shown here in bold:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default 5**

Your default wait time before the system automatically boots into the default is currently set at 10 seconds. You can reduce that somewhat, but be careful not to make it too short. If you make it 0 or 1 second, then you won't have time to change the boot to Ubuntu when you want to.[/QUOTE]


thanks for answering  but I have a duel boot and it wont boot to win xp because of the autochk problem that comes up when trying to start xp instead of ubuntu.just want both to be able to boot.

---

### Post by canadianwriterman on 2006-01-04
Your fstab is set up for dual boot already. What do you mean by "autochk"? I don't get that when I boot with my dual boot Windows XP/Ubuntu system.

---

### Post by mlookn on 2006-01-04
it wont let xp boot it says autochk program not found skipping autocheck then boots to the grub and i can boot ubuntu but not xp something needs to be changed so i can get xp to boot too. thankyou

---

### Post by canadianwriterman on 2006-01-04
Something is strange. autochk is a Windows program as described here:

[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_mdca.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_mdca.asp)

I don't understand why it runs before GRUB. Can anyone else in the forum help out here?

---

### Post by DoorGunner on 2006-01-04
sorry for my late reply back

my grub is actually on fedora core. I didnt load it onto Ubuntu

a handy thing you can do is type the following into shell
> 
$ whereis grub

or 
> 
$ whereis grub.conf

it will give you all your grub file locations.

my fedora one was located /etc/grub.conf it is most likely the same on Ubuntu.

once you are there you can edit it there. I would leave the menu.lst alone.

every time you update from the grub.conf it will update on save and exit.
-----------------------------------------------------------------------------------------------------------------------
> 
$ sudo gedit /etc/grub.conf



default=0
timeout=30
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu

title Windows XP Home Edition SP2+
	rootnoverify (hd0,1)
	chainloader +1

title Fedora Core (2.6.14-1.1653_FC4)
	root (hd0,4)
	kernel /vmlinuz-2.6.14-1.1653_FC4 ro root=/dev/VolGroup00/LogVol00 vga=795
	initrd /initrd-2.6.14-1.1653_FC4.img

title Ubuntu, kernel 2.6.12-10-386 
root    (hd1,0)
kernel  /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd  /boot/initrd.img-2.6.12-10-386
savedefault
boot


Note: this is my grub all you have to do is add in the windows info


[http://stanton-finley.net/fedora_core_4_installation_notes.html](http://stanton-finley.net/fedora_core_4_installation_notes.html)
this is a really nice writeup for grub. The fundamentals will be the same for Ubuntu. Grub is Grub

------------------------------------------------------------------------------------------------------------------------

---

### Post by mlookn on 2006-01-04
grub: /sbin/grub /lib/grub /usr/share/man/man8/grub.8.gz
this is what my where is grub says
when I put in the other sudo part it in comes up blank with nothing in it.so I dont have anything to change.

---

### Post by DoorGunner on 2006-01-04
I appologize.....you were in the right location all along...... enter this command
> 
$ sudo gedit /boot/grub/menu  

If you look up in all that hashed out area. You should see this. we will make it the same as what is recommended in grub.

at the bottom of your file just change the windows portion to read
> 
title Windows
root (hd0,0)
makeactive
chainloader +1


you may have to adjust the hd0,0 for your windows location
do you know what it is? hda,1?

---

### Post by le_jawa on 2006-01-04
Hey mlookn!
First off, don't sweat the grub.conf stuff.  grub.conf is just a symbolic link (something like a shortcut) that Fedora sets up for more conventional naming of the menu.lst file.  You're using Ubuntu, not Fedora so it doesn't apply here.  Editing it is exactly the same as editing menu.lst.  When you try to use gedit to modify /etc/grub.conf, it comes up blank because Ubuntu doesn't have anything named grub.conf in etc, so it assumes you are trying to create a new file named grub.conf.

sudo gives you root access in Ubuntu.
gedit is the GNOME gui text editor.  Think notepad on steroids.

So the command doorgunner gave you is to have you run gedit to edit your grub configuration file while giving you root access (which you need to edit that file; only root has write access to it).

Here's what you need to do if you want to use gedit (which is a good idea):
sudo gedit /boot/grub/menu.lst

It looks like Ubuntu is on your 3rd partition of your first drive, so I'm going to assume that XP is on the same drive, but the first partition.  If that's correct, here's the entry you need to create:

[FONT=Courier New][SIZE=3] title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

[SIZE=2][FONT=Verdana]Of course, the title can be anything you want.  

Also, as doorgunner pointed out, grub counts its drives and partitions starting at 0, so hd0 is the first drive, and ,0 is the first partition.  Adjust either of those numbers to match where XP is installed.

Try that and let us know how it goes!
[/FONT][/SIZE][/SIZE][/FONT]

---

### Post by mlookn on 2006-01-04
im sure its hda1 when you say change windows are you saying get rid of the ms home edition and just use windows or just the hard dive info sorry for problems but trying to learn am a+ cert. so i know win and build comps just a little slow in linix

---

### Post by le_jawa on 2006-01-04
Crap, I'm an idiot.  I didn't see your XP entry at the bottom of your menu.lst file.  What's already there is exactly what you need to boot XP from grub.  Looks like we've been troubleshooting the wrong problem.

Let me make sure I understand the problem.  Look over each step here and tell me if I'm right.

1.  You boot your computer and grub comes up.  
2.  You select Windows XP Home Edition from the list.
3.  XP begins to boot.
4.  XP quickly errors out saying autocheck can't be found and restarts the PC.
5.  You find yourself back in grub. 

Does that sound about right?

---

### Post by mlookn on 2006-01-04
first let me say thankyou guys for the help.
if I look at the hard drive setting it looks the same as you suggest do I put a one or a two in there.
thankyou le_jawa all is appreaciated

by the way does this have a spell checker in it?

---

### Post by mlookn on 2006-01-04
you are right! i've been trying to explain this problem all along hope we can get this fixed 
so i can get on with my learning of linix commands and so on.

---

### Post by le_jawa on 2006-01-04
Here's what gets me: (hd0,0), which is the entry you have now, should be right.  The next partion (hd0,1 in grub-speak or /dev/hda2 according to Linux itself) should be your swap partition, not your XP partition.  hd0,2 (or /dev/hda3) is your root partition for Linux.

As for the help, no problem.  I just hope we can get you going.

And sorry, but I don't see a spell check in this forum app.  :-(

But here's the bad news: it's possible (but we don't know yet) that your Windows partion and/or install have been damaged.  That's why I asked if my "steps" matched your experience.  Look back at those 5 steps and let us know if that's really what happens when you try to boot XP, or if it goes a little differently.

Once I know that, we can troubleshoot from there.

Just to make it clear though, I think your menu.lst is fine.  Grub is doing it's job correctly, I believe.

Actually, here's one more tidbit you can include to give us more info.  Browse to your Windows partion from Linux (to make sure it's mounted),  then open a terminal and run the command   

[FONT=Courier New][SIZE=3]df -Th[/SIZE][/FONT]

And paste the output into your reply.  That'll tell everyone what partions you have mounted on your drive.

---

### Post by mlookn on 2006-01-04
yes the 5 steps are correct on how it is acting.
browse win part in linix and ck to see if mounted dont know anything about mounting or how to ck win thru linix please explain.

---

### Post by le_jawa on 2006-01-04
First off -- sorry about asking you to answer that question on the 5 steps a second time.  I was typing my reply when you posted and said they were right.

As for mounting...  Mounting in UNIX (and therefore Linux) is kind of like mapping a drive in Windows: it's how you make the contents of the drive available to you.  You can mount a Windows partition in Linux so that you can read it just like you would from Windows (well, almost just like it :)).

As I recall, Ubuntu sets itself up so that you already have access to the Windows partition.  There should be an icon for your Windows partition on your desktop already, in the upper-left corner. 

Just double-click that icon to make sure the partition is mounted.  It will open up Nautilus (the GNOME file manager, similar to Windows Explorer) and show you the files on your Windows partition.

So first off, check and see if that works.

If it does, open a terminal and run

[FONT=Courier New][SIZE=3]df -Th[/SIZE][/FONT]

and paste the ouput into your reply.

Let me know if you need more info.

---

### Post by mlookn on 2006-01-05
no such icon on the desktop!

---

### Post by le_jawa on 2006-01-05
Ok, here we go then, a crash course in mounting filesystems in Linux and the Linux filesystem structure.  (My apologies if you already know some or all of this.)

In Windows, you don't have one "root directory", you have several drives (A:, C:, D:, etc) and they aren't tied together at all.  In Linux, they are.  **Everything** in Linux is under one root directory, designated by the / .  One of the directories under your root directory is /mnt, a convenient place to mount other filesystems, such as your Windows partition.  Basically, we're going to make it look like your Windows partition is part of your Linux partition.  Don't worry, this will not change your Windows partition in any way.  It will not become part of your Linux partition, it will only look that way to you while you're in Linux.

So first off, we need to create a mount point -- a place where we will mount, or make available, your windows partition.  Open a terminal, and enter

[FONT=Courier New][SIZE=3] cd /mnt[/SIZE][/FONT]

Once that's done, enter

[FONT=Courier New][SIZE=3] sudo mkdir WinXP[/SIZE][/FONT]

You will be prompted for your password, so enter it.  Now you've created your mount point, so enter 

[FONT=Courier New][SIZE=3] sudo gedit /etc/fstab[/SIZE][/FONT]

/etc is the directory for your configuration files in Linux.  fstab is the filesystem table.  It tells Linux what filesystems to mount.  At the end of that file, create a line that looks like this:

[FONT=Courier New][SIZE=3] /dev/hda1  /mnt/WinXP  ntfs   ro,user,auto,uid=<userid>,gid=<groupid>        0       0[/SIZE][/FONT]

where <userid> is your [COLOR=Red]Linux[/COLOR] user id and <groupid> is your Linux group id.  They are probably the same.

This will allow the system to automount your XP partition and put the icon on your desktop.

Save the file and back in the terminal window enter

[FONT=Courier New][SIZE=3] mount /mnt/WinXP[/SIZE][/FONT]

You should now see an icon on your desktop labled WinXP(it will also always be there after you reboot).  Double click it and let me know if everything looks ok.  In particular does the Windows folder look alright?  Does the System32 folder (inside the Windows folder) look ok?  

Let me know if they do, but also copy and paste the contents of your fstab file, and the output from 

[FONT=Courier New][SIZE=3]df -TH[/SIZE][/FONT]

If you encounter any errors, include the messages too. 

Good luck and let me know how it goes!

---

### Post by mlookn on 2006-01-05
le_jawa this is what I get when I try to mount xp
can't find mnt/winxp in /etc/fstab or etc/mtab
heres my fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0
/dev/hda1 mnt/WINXP ntfs ro,user,auto,uid=bob,gid=bobs 0 0

---

### Post by akiro.yamamoto on 2006-01-06
[QUOTE=mlookn]le_jawa this is what I get when I try to mount xp
can't find mnt/winxp in /etc/fstab or etc/mtab
heres my fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0
/dev/hda1 mnt/WINXP ntfs ro,user,auto,uid=bob,gid=bobs 0 0[/QUOTE]

If you look closely at that last line you will see that it's WINXP... not winxp.
In linux or rather at the console CaSe IS Significant.
Help is completely different to help.... you sEE WHaT I MEAn ;)

---

### Post by le_jawa on 2006-01-06
Excellent catch akiro.yamamoto.  And there is still one other thing, mlookn;  your mnt directory is in your root directory ( / ), so it should be /mnt/WINXP, not mnt/WINXP.  I imagine that's how you created it, so now you just need to add the slash to your mount point in your fstab, so that your entry looks like this:

[FONT=Courier New][SIZE=2] /dev/hda1 **[COLOR=Red]/[/COLOR]**mnt/WINXP ntfs ro,user,auto,uid=bob,gid=bobs 0 0

[FONT=Verdana]Once that's fixed, you should be able to mount your XP partition.  If it fails, paste the error message here so we can see if it's a syntax problem or a partition failure.  If it works, lets see if everything is still intact.
[/FONT][/SIZE][/FONT]

---

### Post by mlookn on 2006-01-06
here is the error it give
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
man this is getting tough !

oh btw when loading ubun today i notice a fail on the start up that said 
failed mounting local file sys

---

### Post by le_jawa on 2006-01-06
Alrighty, so Linux says your Windows partition is not formatted with NTFS.  Either it's FAT32, or it's hosed.  Let's hope for FAT32...

And don't worry about the error on reboot: it's the same error that you got when you tried to mount the Windows partition yourself.  It was just Linux trying to automount it.

By chance did you upgrade to XP from Win98/ME?  If so, the filesystem is certainly FAT32.  In any case, get back into your fstab and change the "ntfs" entry in your fstab to say "vfat" instead (the Windows NT4 name for FAT32).  Also, remove the options "ro", "uid=bob" and "gid=bob".  It wouldn't be a bad idea to change "user" to "users" either."It should now look like this:

[FONT=Courier New][SIZE=2] /dev/hda1 [COLOR=Black]/[/COLOR]mnt/WINXP **[COLOR=Red]vfat[/COLOR]** **[COLOR=Red]users[/COLOR]**,auto 0 0

[FONT=Verdana] Save your changes.  The right-click on your WINXP desktop icon and click "Unmount  Volume".  The icon should disappear.  Then go to your Places menu (near the upper-left corner beside the Applications menu) and click on "Computer".  Double-click on the WINXP icon.  If it mounts, and you can see your stuff, then your Windows partition is ok.

Just in case...  When you try to unmount your Windows partion, if you get an error saying only root can do that, pull up a terminal window and enter[/FONT]

sudo umount /mnt/WINXP

[FONT=Verdana]and enter your password when prompted.  That will unmount the filesystem.

Let us know how it goes, and good luck![/FONT]
[/SIZE][/FONT]

---

### Post by mlookn on 2006-01-06
no it was a clean install, no upgrade, just want you to know before I go any farther
swap file should be fat 32 only

---

### Post by le_jawa on 2006-01-06
Well, then we'll see soon enough.  Try it out and good luck.

---

### Post by mlookn on 2006-01-06
double click winxp icon get error

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted. all blank except the error.

so what do you think ?

---

### Post by le_jawa on 2006-01-06
Not good.  It looks like your Windows partition got fouled up.  I hope you had backups of any essential data (photos, documents, etc).  Your best bet at this point is to re-install Windows.  Boot from the XP CD. When it asks you if you want to repair or install, choose install.  Afterwards, if it finds your old XP install, it will prompt you to perform a fresh install or a repair install.  Select repair install if it gives you the option.  Either way, install to the same partition where it was.  Recreate it if you have to.

Sorry to be the bearer of bad news.  I hope you didn't lose anything of importance.

This isn't a Windows forum, but I'll be happy to help you with the install if you need it.

---

### Post by mlookn on 2006-01-06
so then I will lose ubun is there an uninstall for ubun

---

### Post by le_jawa on 2006-01-06
DOH!  I forgot one very important detail to finish the job.  Once you re-install windows, You will no longer be able to boot Linux without a seperate disk (but you won't lose Ubuntu, it will still be there if you do Windows right) because  Windows will re-install its boot manager.  Once you have windows humming along again, boot your PC from your live CD (if you have it) or from a Linux rescue CD.  Mount your root partition (/dev/hda3) and run

[FONT=Courier New] /sbin/grub[/FONT]

Once inside the grub command line enter:

[FONT=Courier New] root (hd0,2)
[/FONT] 
then enter 

[FONT=Courier New] setup (hd0)
[/FONT] 
and exit grub.  grub will re-install itself, and you will be back where you wanted to be.  Just reboot.

Once again, good luck and let us know if you need further help.

---

### Post by mlookn on 2006-01-06
le_jawa  you mean (if) I can do a repair and maybe do fixmbr I do have both cds
live and full setup because live is just a image of ubun to run on win right?

just want to say you've been very helpful and thankyou for trying to save my comp
even if im 58 and sill trying to learn ubun.

god bless and hope to see you again.

if I decide to dual boot again any ideas about setting up the the hard drive which is first and last 
80 gig

---

### Post by le_jawa on 2006-01-07
> **mlookn]le_jawa  you mean (if) I can do a repair and maybe do fixmbr I do have both cds
live and full setup because live is just a image of ubun to run on win right?
[/quote]
Oh wow, I really need to work on my communication skills...  said:**
> .  Don't touch them!  They're fine!  You will also see that the first partition is marked as [Damaged or unknown filesystem].  Use the arrow keys to select it, and hit D to delete the partition.  You will be asked a couple of times if that's what you want to do, confirm it using whatever keys it specifies (I don't remember for certain).

Now you should be back at the partition screen and your first partition should be marked [Free Space] or something along that line.   Hit C to create a new partition.  Accept the size (it will take the whole partition) and select NTFS or FAT32 as your filesystem.  Linux can read and write to FAT32 (and cannot yet write to NTFS), but NTFS is more robust and efficient, so it's better for Windows.  It's your choice.  Use quick format if you think your drive is in good shape, don't if you want the format to check your drive too.

Just follow the prompts from there and the rest will be simple.  As part of the install, Windows will put it's boot loader back on (so fixmbr will be unnecessary), so Ubuntu won't boot anymore, but it's still there.

So now Windows is installed and working.  Take out your Windows install CD and reboot to test it briefly.  You'll notice that grub (the Linux bootloader) is gone and you can no longer boot into Linux.  That's ok.  You can't boot into Linux yet, but it's still there and ready to go.  So now we need to reinstall grub and by doing that, make Linux bootable again along with Windows.  If you have your Ubuntu Live CD, use it.  If not, get a rescue cd such as this one: 

[http://sourceforge.net/projects/ivrescue/]("http://sourceforge.net/projects/ivrescue/")

Boot the cd and create a mount point for your system just like we did for Windows (maybe /mnt/linuxrescue).  Use the mount command to mount it once you've created the mount point.  It should look like this:

[FONT="Courier New"]mount /dev/hda3 -t ext3 /mnt/linuxrescue[/FONT]

If you use a rescue CD, it may mount it for you and will probably use a mount point by a different name.  Pay attention to that name and use it if the CD automounts your Linux partition.

Once your parition is mounted, run

[FONT="Courier New"]/mnt/linuxrescue/sbin/grub[/FONT] (or whatever directory the rescue CD uses if it's not /mnt/linuxrescue)

Once you get the grub prompt enter

[FONT="Courier New"]root (hd0,2)[/FONT]

then on the next prompt enter

[FONT="Courier New"]setup (hd0)[/FONT]

Make sure you include the spaces in both lines.  It won't work without the space between the command and the first paranethesis "( ".

Shtudown the Linux rescue system, remove the Linux cd and reboot.  Grub, Windows and Linux are now all working fine.


[quote=mlookn]just want to say you've been very helpful and thankyou for trying to save my comp
even if im 58 and sill trying to learn ubun.

god bless and hope to see you again.

if I decide to dual boot again any ideas about setting up the the hard drive which is first and last 
80 gig

If you decide to start from scratch with the same drive or a new one, definitely install Windows first.  However, you're going to use the same drive, just follow the instructions above and you'll save some time since you won't have to re-isntall Ubuntu Linux.

There is one other thing I wanted to mention along this line.  If you have any data on your XP partition that you need to recover, it is still possible, for a price.  The data is still on your drive, as long as you don't overwrite it by installing Windows again.  You can buy recovery software and do it yourself, or send your drive off to a service to have them do it for you (but this can get expensive).  I just wanted you to know that you do have options.

As for the rest, I would help you whether you were 58 or 18. :D  If anything, I'm impressed that you're attempting Linux at all.  It's a lot to learn, but I think you'll enjoy it.

May God bless you also, and may you always stay close enough to him that He can do so.

Good luck with all this, and let me know if I can help you more with this.  If anything else comes up, just post a new thread to the forum.

---

### Post by mlookn on 2006-01-07
le_jawa I followed what you advised and came up with two drives in windows c an f   f has my files and c says raw no listing of any thing im just woundering if i should just blow the whole drive and start over.

---

### Post by le_jawa on 2006-01-07
[quote=mlookn]le_jawa I followed what you advised and came up with two drives in windows c an f   f has my files and c says raw no listing of any thing im just woundering if i should just blow the whole drive and start over.[/quote] 
So you did get some back?!  Excellent!  Your best bet at this point is to backup any data you want to keep to CD, Zip, a pendrive, another hard drive... something.  The stuff listed below may still lose data.  (Actually, #2 will result in complete data loss.  That's basically the idea.)

As for your C: and F: drive, the partition table on that drive has gotten a bit corrupted it sounds like.  You've got a couple of options at this point:

1.)  Use Partition Magic (the regular program, not the table editor) to merge your C: and F: drives into one C: drive.  If all goes well, Windows will be ready to go at that point and all you need to do is re-install GRUB (following the procedure I gave you earlier).  Once that's done, you're set!  Windows and Ubuntu Linux should both boot fine.

2.) You can simply remove all partitions and start over.   The drive itself should be fine and can be reused either way.  Once you have Windows reinstalled, you may want to run scandisk just to be on the safe side.

Either way, best of luck with it.  I'm glad you got this far.  Recovering your old stuff is a huge plus.  Come on back if you still need a hand.

---

### Post by mlookn on 2006-01-08
le_jawa heres the good news, I blew away the hd dv reinstalled xp and then ubun,
everything is up and running with no problems, boot bothways the only thing it didn't do was put an xp icon the desk top. but thats ok now I can start to learn how ubun runs and works, do I have to mount stuff to get things to work, or just look around and learn as I go. again thankyou for your ongoing help.
mlookn  oh btw what is the firefox desktop suppose to look like all I got is a bunch of writing explaining about ubuntu.

---

### Post by le_jawa on 2006-01-09
> **mlookn]le_jawa heres the good news, I blew away the hd dv reinstalled xp and then ubun, everything is up and running with no problems, boot bothways...[/quote] 
Excellent! I'm glad to hear you have a system that runs to your satisfaction. It's always nice when things actually work right! :)

[quote=mlookn] the only thing it didn't do was put an xp icon the desk top.[/quote] 
No biggie there. Just go back through this thread and retrace your steps. You did it once, you should have no trouble doing it again.

[quote=mlookn]but thats ok now I can start to learn how ubun runs and works, do I have to mount stuff to get things to work, or just look around and learn as I go. again thankyou for your ongoing help.[/quote] 
That's what it's all about -- monkey and learn. If you're able to, you may want to pickup a book or two to help you learn faster. In the end though, it's the experience of doing that helps you learn the most about the "how to do". The books are best for accelerating that learningand for learning why you're doing the the things you do and how they work.

As for needing to mount things, you only "need" to mount your Windows partition if you want access to your Windows files.  I had you do it earlier as a troubleshooting step said:**
> mlookn oh btw what is the firefox desktop suppose to look like all I got is a bunch of writing explaining about ubuntu. 
If you're used to Windows and Internet Explorer, I think you'll really enjoy Firefox. It's not a desktop, it's a web browser. It serves the same purpose as IE, it's just better in pretty much every regard. The page you pulled up with all the info is just a file on your hard drive that the folks at Ubuntu put on their to give you some info and help. Once you're connected to the Internet with Ubuntu, use it the same way you would Internet Explorer; visit the same sites, read your email via a webmail page, whatever you did with IE. As a side note, there is a version of Firefox for Windows, too.

If I may recommend one more piece of software, Open Office.org is well worth looking at. If you use MS Office for creating documents, etc., Open Office.org is a really slick free alternative. It's already installed with Ubuntu, and like Firefox, it's available for Windows and Linux (as well as the Macintosh). 

So play around with Ubuntu; I hope you enjoy learning Linux with it. And of course, drop a note in the forum if you need help again.

Good luck, and have fun!

---

