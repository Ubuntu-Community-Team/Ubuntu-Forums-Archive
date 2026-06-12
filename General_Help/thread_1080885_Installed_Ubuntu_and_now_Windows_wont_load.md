---
title: "Installed Ubuntu and now Windows wont load"
date: 2009-02-25
forum: General Help
---

### Post by thermobee on 2009-02-25
Ok i have two hard drives. One is 80gb and the second one is 40gb. I wanted to get a clean install so i installed XP and formatted both HDs. Then I ran the liveCD and went into ubuntu. From there i partioned the HDs like this:

dev/sda1 primary ntfs WinXP 38GB
dev/sda2 primary ext3 Ubuntu 40GB
dev/sda3 primary swap 2GB
dev/sdb1 extended
dev/sdb2 logical ntfs Shared Files 40gb

At the end of the pre install set-ups i checkmarked Install boot loader and device for boot loader installation dev/sda

Now when i start the PC and click Esc to get into the options there are 5 different Ubuntu options ( sorry cant remember the exact names) but no windows. From the guide that I read I was left with the impression that Ubuntu's GRUB will allow me to select XP if i want.

Any thoughts would be appreciated.):P

---

### Post by taurus on 2009-02-25
Are you sure you didn't wipe out windows during the installing process?  Open a terminal and post the output of this command here.

```
sudo fdisk -lu
```
And since you want to share the second harddrive between windows and Ubuntu, why even making it a logical partition although it doesn't really matter.

---

### Post by thermobee on 2009-02-25
Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    62203679    31101808+   7  HPFS/NTFS
/dev/sda2   *    62203680   149902514    43849417+  83  Linux
/dev/sda3       149902515   156296384     3196935   82  Linux swap / Solaris

no it seems to be still there

---

### Post by thermobee on 2009-02-25
The only reason why im even trying to solve this is because my parents ocasionally need XP. If it was just up to me i would've gotten rid of it

---

### Post by taurus on 2009-02-25
What does your /boot/grub/menu.lst look like then?

p.s.  Interesting that your ntfs partition doesn't start at the beginning of the drive, 1.  Is there a recovery (hidden) partition for windows?

---

### Post by thermobee on 2009-02-25
yeah both my drives start at 63 i dont know why. I will restart now and check out the menu list

---

### Post by thermobee on 2009-02-25
Here it is:

Ubuntu 8.10, kerner 2.6.27-11-generic
Ubuntu 8.10, kerner 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kerner 2.6.27-7-generic
Ubuntu 8.10, kerner 2.6.27-7-generic (recovery mode)
Ubuntu, memtest 86+

---

### Post by taurus on 2009-02-25
What does the actual file, /boot/grub/menu.lst, look like though?

```
cat /boot/grub/menu.lst
```

Maybe you want to install startupmanager and use it to reconfigure GRUB, adding windows option in there if it allows you to.

```
sudo apt-get update
sudo apt-get install startupmanager
gksudo startupmanager
```

---

### Post by thermobee on 2009-02-25
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ca032f1f-a571-46fc-9221-ef1d942f53aa ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=ca032f1f-a571-46fc-9221-ef1d942f53aa

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ca032f1f-a571-46fc-9221-ef1d942f53aa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca032f1f-a571-46fc-9221-ef1d942f53aa ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ca032f1f-a571-46fc-9221-ef1d942f53aa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca032f1f-a571-46fc-9221-ef1d942f53aa ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ca032f1f-a571-46fc-9221-ef1d942f53aa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca032f1f-a571-46fc-9221-ef1d942f53aa ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ca032f1f-a571-46fc-9221-ef1d942f53aa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca032f1f-a571-46fc-9221-ef1d942f53aa ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ca032f1f-a571-46fc-9221-ef1d942f53aa
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by thermobee on 2009-02-25
yeah i dont see how you can add windows to it

---

### Post by taurus on 2009-02-25
Edit your /boot/grub/menu.lst and add the following lines to the end of it, after the ### END DEBIAN AUTOMAGIC KERNELS LIST.

```

title Windows XP
root (hd0,0)
makeactive
chainloader +1

```
Save it and reboot.  By the way, might want to put a # in front of the **hiddenmenu** to comment it out so you would see a GRUB menu when you turn on your machine instead of pressing the ESC within 3 seconds to bring it up.

```
#hiddenmenu
```

---

### Post by thermobee on 2009-02-25
> **taurus said:**
> Edit your /boot/grub/menu.lst and add the following lines to the end of it, after the ### END DEBIAN AUTOMAGIC KERNELS LIST.

```

title Windows XP
root (hd0,0)
makeactive
chainloader +1

```
Save it and reboot.  By the way, might want to put a # in front of the **hiddenmenu** to comment it out so you would see a GRUB menu when you turn on your machine instead of pressing the ESC within 3 seconds to bring it up.

```
#hiddenmenu
```
Im sorry i dont know how to edit it.

---

### Post by taurus on 2009-02-25
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by thermobee on 2009-02-25
> **taurus said:**
> ```
gksudo gedit /boot/grub/menu.lst
```
Do I paste the whole thing in there and then add the 4 lines or just add the 4 lines and save?

---

### Post by taurus on 2009-02-25
Scroll down to the end of the file (long file) and paste those four lines at the end.  Save it and reboot.

And since you are probably not going to comment out the hiddenmenu, you have to press the ESC key to bring up the menu then.

---

### Post by thermobee on 2009-02-25
> **taurus said:**
> Scroll down to the end of the file (long file) and paste those four lines at the end.  Save it and reboot.

And since you are probably not going to comment out the hiddenmenu, you have to press the ESC key to bring up the menu then.
Pressing the Esc key doesnt bother me, but something else does. When the lst came up it was completely empty.

---

### Post by taurus on 2009-02-25
Can you show me the exact command that you typed in to a terminal?

---

### Post by thermobee on 2009-02-25
> **taurus said:**
> Can you show me the exact command that you typed in to a terminal?

gksudo gedit /boot/grub/menu.lst

waited a bit then *lst(/boot/grub/menu) -gedit popped up, kinda looks like a word processor and it was blank

---

### Post by taurus on 2009-02-25
Look at your post #9 again.  That is what /boot/grub/menu.lst looks like.  I assume back then you ran this command to display it, right?

```
cat /boot/grub/menu.lst
```
Now, replace the **cat** with **gksudo gedit**, i.e.,

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by HuaiDan on 2009-02-25
in the terminal after the "$", type   

gksudo gedit /boot/grub/menu.lst

Then press enter. Then type your password. Then press enter.

A text editor will open the file, menu.lst.  There's several lines of code in there, most of it is commented out (##).  Somewhere at the end look for 

title Windows XP
root (hd0,0)
makeactive
chainloader +1

If it's not there, put it there. You can put it atthe top if you want Windows to be at the top of the list and therefore default.

Save the file.  Reboot. Report back.

---

### Post by thermobee on 2009-02-25
> **taurus said:**
> Look at your post #9 again.  That is what /boot/grub/menu.lst looks like.  I assume back then you ran this command to display it, right?

```
cat /boot/grub/menu.lst
```
Now, replace the **cat** with **gksudo gedit**, i.e.,

```
gksudo gedit /boot/grub/menu.lst
```
ok it worked and the windows xp option is there. this is the message i get NTLDR is missing.

---

### Post by thermobee on 2009-02-25
any idea what that is?

---

### Post by thermobee on 2009-02-25
ok so windows is missing the boot loader. how do i fix it?

---

### Post by thermobee on 2009-02-25
do you think this would work?

   1.  Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter, which in this case is "e." This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

---

### Post by Rabid Moth on 2009-02-26
Hi. First check to make sure that when your pc starts up that you can choose boot options. If you have 2 hard drives then what you could do, it's what I like do, is open your case and unplug one of the hard drives. Install Windows on the hard drive that is still connected. After you have Windows installed, unplug it & plug in your other hard drive & install Ubuntu onto it. Then plug them both in. When the pc restarts you hit whatever key lets you do a boot choice, mine is Esc, and then pick the hard drive you want to boot into. 

This makes it very nice on user's machines that are really new to Linux because it wont do anything to their Windows if something gets messed up while they're doing things on Linux.

This of course is just a personal opinion but a good way to go if you are unsure of Linux and do not want to lose and reinstall Windows.

---

### Post by thermobee on 2009-02-26
> **Rabid Moth said:**
> Hi. First check to make sure that when your pc starts up that you can choose boot options. If you have 2 hard drives then what you could do, it's what I like do, is open your case and unplug one of the hard drives. Install Windows on the hard drive that is still connected. After you have Windows installed, unplug it & plug in your other hard drive & install Ubuntu onto it. Then plug them both in. When the pc restarts you hit whatever key lets you do a boot choice, mine is Esc, and then pick the hard drive you want to boot into. 

This makes it very nice on user's machines that are really new to Linux because it wont do anything to their Windows if something gets messed up while they're doing things on Linux.

This of course is just a personal opinion but a good way to go if you are unsure of Linux and do not want to lose and reinstall Windows.
The thing is i just reinstalled both windows and ubuntu so i can have a clean install and make sure everything works well. Now boot loader for xp in corrupted or not working and im aftraid that i repair xp with the CD it will take over like it did before and xp will just boot automatically as soon as I start the computer.

---

### Post by caljohnsmith on 2009-02-26
In order to see which Windows boot files might be missing (like ntldr), how about posting:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
cat /mnt/boot.ini
```
And we can work from there if you want.

---

### Post by thermobee on 2009-02-26
> **caljohnsmith said:**
> In order to see which Windows boot files might be missing (like ntldr), how about posting:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
cat /mnt/boot.ini
```
And we can work from there if you want.
I would love that give me a second.

---

### Post by thermobee on 2009-02-26
total 1573116
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 AUTOEXEC.BAT
drwxrwx--- 1 root plugdev          0 2009-02-25 17:05 $AVG8.VAULT$
drwxrwx--- 1 root plugdev          0 2009-02-25 16:40 Config.Msi
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 CONFIG.SYS
drwxrwx--- 1 root plugdev       4096 2009-02-24 12:48 Documents and Settings
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 IO.SYS
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 MSDOS.SYS
-rwxrwx--- 1 root plugdev 1610612736 2009-02-25 16:56 pagefile.sys
drwxrwx--- 1 root plugdev       8192 2009-02-25 16:35 Program Files
drwxrwx--- 1 root plugdev          0 2009-02-24 23:05 RECYCLER
drwxrwx--- 1 root plugdev       4096 2009-02-24 12:47 System Volume Information
drwxrwx--- 1 root plugdev       4096 2009-02-25 17:29 ubuntu
drwxrwx--- 1 root plugdev      36864 2009-02-25 16:43 WINDOWS
-rwxrwx--- 1 root plugdev     192307 2008-10-27 13:37 wubildr
-rwxrwx--- 1 root plugdev       8192 2008-10-27 13:37 wubildr.mbr

---

### Post by thermobee on 2009-02-26
the second line doesnt work
this is what comes up: cat: /mnt/boot.ini: No such file or directory

---

### Post by Vaphell on 2009-02-26
i had similar problem once, after messing up with partitions i installed XP on a non-primary one, then proceeded with ubuntu. I found out later that boot.ini is located on another drive (D: from xp point of view to be exact). I had to modify grub menu entry to point that partition.

---

### Post by thermobee on 2009-02-26
> **thermobee said:**
> total 1573116
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 AUTOEXEC.BAT
drwxrwx--- 1 root plugdev          0 2009-02-25 17:05 $AVG8.VAULT$
drwxrwx--- 1 root plugdev          0 2009-02-25 16:40 Config.Msi
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 CONFIG.SYS
drwxrwx--- 1 root plugdev       4096 2009-02-24 12:48 Documents and Settings
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 IO.SYS
-rwxrwx--- 1 root plugdev          0 2009-02-24 12:43 MSDOS.SYS
-rwxrwx--- 1 root plugdev 1610612736 2009-02-25 16:56 pagefile.sys
drwxrwx--- 1 root plugdev       8192 2009-02-25 16:35 Program Files
drwxrwx--- 1 root plugdev          0 2009-02-24 23:05 RECYCLER
drwxrwx--- 1 root plugdev       4096 2009-02-24 12:47 System Volume Information
drwxrwx--- 1 root plugdev       4096 2009-02-25 17:29 ubuntu
drwxrwx--- 1 root plugdev      36864 2009-02-25 16:43 WINDOWS
-rwxrwx--- 1 root plugdev     192307 2008-10-27 13:37 wubildr
-rwxrwx--- 1 root plugdev       8192 2008-10-27 13:37 wubildr.mbr
can anyone figure out the problem from this?

---

### Post by caljohnsmith on 2009-02-27
Your Windows partition is missing its necessary boot files, so probably what happened is Windows had its boot files in another primary NTFS/FAT partition that you subsequently deleted when you installed Ubuntu. Is that maybe what happened? Regardless of whether that is what happened or not, you'll need to replace Windows' three necessary boot files before you'll have any chance of getting Windows to boot again. Since you are hesitant to use your Windows CD, I've attached the three necessary boot files you need to this post in a file called "WinXP_boot_files1.zip" and made sure the "boot.ini" file is configured for your particular setup; all you need to do is download the attached zip file to your Ubuntu desktop and do the following commands:
```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Then reboot, select Windows from your Grub menu, and let me know exactly what happens. We can work from there if necessary.

---

### Post by thermobee on 2009-02-27
any one?

---

### Post by thermobee on 2009-02-27
> **caljohnsmith said:**
> Your Windows partition is missing its necessary boot files, so probably what happened is Windows had its boot files in another primary NTFS/FAT partition that you subsequently deleted when you installed Ubuntu. Is that maybe what happened? Regardless of whether that is what happened or not, you'll need to replace Windows' three necessary boot files before you'll have any chance of getting Windows to boot again. Since you are hesitant to use your Windows CD, I've attached the three necessary boot files you need to this post in a file called "WinXP_boot_files1.zip" and made sure the "boot.ini" file is configured for your particular setup; all you need to do is download the attached zip file to your Ubuntu desktop and do the following commands:
```
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Then reboot, select Windows from your Grub menu, and let me know exactly what happens. We can work from there if necessary.

tod@tod-desktop:~/Desktop$ sudo mv boot.ini ntldr NTDETECT.COM /mnt
mv: cannot stat `boot.ini': No such file or directory
mv: cannot stat `ntldr': No such file or directory
mv: cannot stat `NTDETECT.COM': No such file or directory

---

### Post by caljohnsmith on 2009-02-27
Did you first download the WinXP_boot_files1.zip file first to your desktop? Did you do the command to unzip it? How about posting the entire terminal session so I can see the output of all the commands (copy/paste it to your post).

---

### Post by thermobee on 2009-02-27
> **caljohnsmith said:**
> Did you first download the WinXP_boot_files1.zip file first to your desktop? Did you do the command to unzip it? How about posting the entire terminal session so I can see the output of all the commands (copy/paste it to your post).
I mustve mispelled it the first time. It worked and im actually posting from XP now. Thank you very much I really appreciate your help

---

### Post by thermobee on 2009-02-27
now if you could only tell me how to reinstalled flash player, cause i cant watch youtube videos or anything streaming online for that matter :D

---

### Post by miegiel on 2009-02-27
IIRC flash is in the restricted or medibuntu repositories. I bet you can find the info on the forum somewhere. :twisted: Search "restricted" and/or "medibuntu".

---

### Post by thermobee on 2009-02-28
> **miegiel said:**
> IIRC flash is in the restricted or medibuntu repositories. I bet you can find the info on the forum somewhere. :twisted: Search "restricted" and/or "medibuntu".
you are right i cant. ill try your suggestion

---

