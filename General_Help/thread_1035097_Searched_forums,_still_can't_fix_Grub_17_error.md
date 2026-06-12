---
title: "Searched forums, still can't fix Grub 17 error"
date: 2009-01-09
forum: General Help
---

### Post by missbliss on 2009-01-09
hi all, i have searched the forums for a solution to my Grub 17 error but have had no luck.

I had a dual boot set up for Ubuntu 8.10 and Vista.  I believe my problem occured when I chose to hibernate Ubuntu.  At that point i started messing with things and now i seem to have gotten rid of Vista altogether and can only boot from my live Ubuntu disc.

my system looks like this:  (sorry, i can't remember which command got me this info)

Device Boot    System

/dev/sda1      Linux
/dev/sda2      Extended
/dev/sda5      Linux swap/Solaris


There is of course "Start", "End", "Blocks" and "Id" in between this information.


any help???

---

### Post by Tim Sharitt on 2009-01-09
Reinstalling grub may do the trick. The guide is here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by deltaromeo on 2009-01-09
Use [Super GRUB Disk]("http://www.supergrubdisk.org/") and you will never look back!  It has got me out of a lot of GRUB problems, I can't praise it enough

---

### Post by caljohnsmith on 2009-01-09
Does your computer use an AMD64 processor? If so, you might have fallen victim to this bug since you tried to hibernate Ubuntu:

[http://ubuntuforums.org/showthread.php?t=927831](http://ubuntuforums.org/showthread.php?t=927831)

Also, have you tried doing an file system check on the linux partition? How about from the Live CD try:
```
sudo fsck -yCM /dev/sda1
```
And please post the output. Also, let me know if the above bug might apply to your situation.

---

### Post by missbliss on 2009-01-09
> ubuntu@ubuntu:~$ sudo fsck -yCM /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

so, that's what i got when i ran that command.  i am still going to check out the provided links, too.

i should also add that i have run a complete disk check and it came up fine.

---

### Post by missbliss on 2009-01-09
> **Tim Sharitt said:**
> Reinstalling grub may do the trick. The guide is here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
as far as this goes i get an error 15 on both the first and second command.  :-(

i gather that i am on sda and not hd, so i put in:

root (sda1,2)

and i get:

error 23  error while parsing number

---

### Post by caljohnsmith on 2009-01-09
So it appears your Ubuntu partition did get corrupted as a result of the hibernation. How about trying [this guide]("http://ubuntuforums.org/showpost.php?p=5806996") in order to get the fsck to complete successfully, except replace "sda5" in all the commands with "sda1" since your Ubuntu partition is sda1. If you run into problems, please post the output of all the commands.

---

### Post by missbliss on 2009-01-09
```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep superblock
dumpe2fs 1.41.3 (12-Oct-2008)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
ubuntu@ubuntu:~$ 

```

oh, but i do have a column written down labeled "Blocks" when i got the Device Boot (can't remember what command i did for this.)  anyway for /dev/sda1 it has the "Blocks" as 303660598+


BIG OOPS!!  please ignore what i first wrote, i accidentally did the second command first.  this is what i got when i did the first command:

```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | -i "block size"
dumpe2fs 1.41.3 (12-Oct-2008)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda1
bash: -i: command not found
ubuntu@ubuntu:~$ 
```

---

### Post by missbliss on 2009-01-10
up, in case i can get more info.  :-)

---

### Post by caljohnsmith on 2009-01-10
How about instead trying:
```
sudo apt-get install testdisk
sudo testdisk
```
Choose "No Log", "Proceed", "Intel", "Advanced", then select your sda1 linux partition using the up/down arrow keys, and choose "superblock". If that gives a list of the superblocks for sda1, then you can use that in the commands in the previous link I posted. But if testdisk can't give you any superblocks for your Ubuntu partition, I think you're probably looking at having to do a reinstall. If you have some really important data that you want to try and recover from the partition, you could use "photorec", which is part of the testdisk package. Let me know how it goes though.

---

### Post by missbliss on 2009-01-11
thanks a ton for the response.  i will try this when i get home.

---

### Post by missbliss on 2009-01-11
[code]ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
[/code

i have downloaded supergrubdisk on a friend's pc and am going to try that when i burn it and bring it to my house, though.

---

### Post by caljohnsmith on 2009-01-11
How about checking to make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then try downloading and running the testdisk program again. I think that might be why apt-get said it couldn't find the testdisk package.

---

### Post by missbliss on 2009-01-11
i checked the universe box in software sources then entered the same cmd in to the terminal, but it yielded the same result.

---

### Post by Tim Sharitt on 2009-01-11
If you have just enabled the universe repos, you will need to update your package list.
```
sudo apt-get update
```
Then try installing it.

---

### Post by missbliss on 2009-01-12
alright, i'm about ready to give up.

if i get the recovery disks for my laptop (HP) will that work?  or will i still be facing the same problem?

---

### Post by caljohnsmith on 2009-01-12
If you still want to try using testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your Ubuntu desktop, and then do:
```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
Let me know if that works or not.

---

### Post by Dustin2128 on 2009-01-12
I had a grub error as well, reinstalling ubuntu, but with 8.04 instead of 8.10 worked for me. Don't know if that'd be an option for you though...

---

### Post by missbliss on 2009-01-13
> **caljohnsmith said:**
> If you still want to try using testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your Ubuntu desktop, and then do:
```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
Let me know if that works or not.

```
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ tar xvf testdisk-6.10.linux26.tar.bz2
testdisk-6.10/
testdisk-6.10/NEWS
testdisk-6.10/README
testdisk-6.10/COPYING
testdisk-6.10/INFO
testdisk-6.10/ico/
testdisk-6.10/ico/photorec.ico
testdisk-6.10/ico/testdisk.ico
testdisk-6.10/linux/
testdisk-6.10/linux/l/
testdisk-6.10/linux/l/linux
testdisk-6.10/linux/readme.txt
testdisk-6.10/linux/photorec.1
testdisk-6.10/linux/photorec_static
testdisk-6.10/linux/testdisk_static
testdisk-6.10/linux/testdisk.1
testdisk-6.10/ChangeLog
testdisk-6.10/AUTHORS
testdisk-6.10/THANKS
testdisk-6.10/documentation.html
ubuntu@ubuntu:~/Desktop$ sudo testdisk-6.10/linux/testdisk_static

```

this is what i got....  i'm so lost, i'm sorry!!!!

---

### Post by missbliss on 2009-01-17
So, just one last question, since I don't think I've got the savvy to fix it at this point.

(I still need to try supergrub disk)

Question:  If I purchase my HP laptop Recovery Disks from HP will those solve my problem?  Or will I still be faced with road blocks since it sound like the MBR is confused?

Once again, thanks so much for the help.  The ubuntu community rules!  I'm not giving up on Linux just cause of this by the way.  I'm pretty sure I've identified why I got in this situation, so chances of it happening again I *hope* are low.

---

### Post by Universal344 on 2009-01-17
OK, you could try this, but I don't know if it will work.  Get the recovery CD and if it the same as the recovery environment on my vista install cd than you can use it to write a brand new MBR to your HD.  Just go to the recovery environment and open a command line and type bootrec.exe /fixmbr to write a new MBR.  I think htat is the command but should definately check first.  Also there is a command to write a new boot sector but I have not used it so I don't know what it will do.  Then you could try reinstalling GRUB.  Also, if you did not get rid of your NTFS and it just seemed to disappear than it just be corrupt and you may be able to fix it (maybe).

EDIT: once you've written a new MBR it may be worth giving another bootloader a try like lilo.  However, since I have not used it personally I do not know if it will correctly detect all your OSs.

---

### Post by Frantic_Earthling on 2009-01-17
I may be entirely wrong but if my memory serves me right, I experienced grub error 17 in the past and it was due to the fact that for reasons that I still cannot explain, my BIOS decided to boot on my second HD which of course held only data.

All I had to do was to get into the BIOS set up and reset the boot sequence in the right order.

Maybe the same in your case?

---

### Post by upchucky on 2009-01-17
hp disks wont help, u are custom building ubuntu for the pc.

get advanced supergrub, and knoppix.

advanced supergrub has a few more bells and whistles to help fix grub errors and master boot files for all boot situations.

Knoppix has both partition editors available to help with dual boot scenarios and can fix both windows and linux files. there are some rare circumstances where u may need both partition editors to fix partitions. it also lets you edit the boot records and other loader files on a non responsive system to get them working again.

---

### Post by missbliss on 2009-01-20
Okay, guys, here's the deal:

On a whim I tried to reinstall Ubuntu and this time it worked.  There was one error message which I didn't write down (d'oh!) but I chose "skip" and everything seemed to go smoothly.  

I rebooted w/o the CD, went through GRUB fine, entered my username and password then the pale orange screen showed briefly, then a blank (black) screen came up and I can hear the start up music, and see a regular cursor and that's it.  Almost like I just can't see any graphics.

Don't know why the sudden change, but does anyone have any suggestions from this point???  



As always, thanks for taking the time to look!

---

### Post by missbliss on 2009-01-20
up.........

---

### Post by missbliss on 2009-01-20
Another reinstall solved the problem.  Somehow I feel like it had something to do with this: 
> **missbliss said:**
> ```
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ tar xvf testdisk-6.10.linux26.tar.bz2
testdisk-6.10/
testdisk-6.10/NEWS
testdisk-6.10/README
testdisk-6.10/COPYING
testdisk-6.10/INFO
testdisk-6.10/ico/
testdisk-6.10/ico/photorec.ico
testdisk-6.10/ico/testdisk.ico
testdisk-6.10/linux/
testdisk-6.10/linux/l/
testdisk-6.10/linux/l/linux
testdisk-6.10/linux/readme.txt
testdisk-6.10/linux/photorec.1
testdisk-6.10/linux/photorec_static
testdisk-6.10/linux/testdisk_static
testdisk-6.10/linux/testdisk.1
testdisk-6.10/ChangeLog
testdisk-6.10/AUTHORS
testdisk-6.10/THANKS
testdisk-6.10/documentation.html
ubuntu@ubuntu:~/Desktop$ sudo testdisk-6.10/linux/testdisk_static

```

this is what i got....  i'm so lost, i'm sorry!!!!
since it was one of the only things that yielded a result.  I really don't know....  Should I delete the post or mark as solved???  

Either way, I appreciate the help and am sooooooooooo happy my laptop is back!!!!!!!

---

