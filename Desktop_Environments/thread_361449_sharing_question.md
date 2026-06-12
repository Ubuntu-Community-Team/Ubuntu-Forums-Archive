---
title: "sharing question"
date: 2007-02-14
forum: Desktop Environments
---

### Post by PrismaticKen on 2007-02-14
I set up four identical 250GB Hitachi hard drives in a software raid (configured upon installing the OS)....my server also has a 40GB IDE drive (seagate, which the OS apparently installed to).  Either way, I just want to know....How do I share my quad-hitachi soft raid on my network as one big share?  Where is it?  Why is it that is seemingly every linux distro there isn't any kind of listing that shows you only the drives you have in your system, something similar to the 'My Computer' of Windows.  This is my first real time using linux so I'm completely in the dark.  The last few times I tried linux, (Suse 10, Slackware, and Slax) they gave me very silly error messages.  Ubuntu so far has been the most reasonable linux distro by far, and if I can figure out a few more things...I might even prefer it over OS X.

Anyway, back to the core question...how do I share my software Raid over a samba network in Xubuntu 6.1?   Thanks

---

### Post by airtonix on 2007-02-14
/dev/hda is your first harddrive, which isnt listed as an item in a tree....rather it is the "filesystem" that your system folders and file exist on ( if you used the default partitioning durin setup taht is)

for my system.....i partitioned my home folder to another drive, so when i re-install after going "config trigger happy" i keep my entire profile for gnome desktop and everything else there...

recently i started putting my  /var/www on  yet another drive.

to do this :

1- physically install the harddrive(s)
2- open up the disk-manager (System -> Administration -> Disks)
3- you "might" see your raid array listed here im not sure but usually all volumes (disks ie cdrom, dvdrom, ipod, harddrive, usb stick, etc etc) are listed in the left hand coloumn.
4- if your array is there (as one item or more) then you should be able to click it and view more information on the right hand side of the application.
5- if its not as one volume, then your going to have to re-plan your public media sharing plan. ie use symbolic links and share one folder that list symbolic links to the different volumes.
6- if it is. then you can specify where the drive will be accessed from in the "filesystem"


To clear up some confusion you may have here about the way devices are treated in windows and linux....

in linux....:
 a folder is a file is a file is a file is a file is a file is a file.
 a device is a is a file is a file is a file is a file is a file.
 everything is a file is a file is a file is a file is a file.

the exception is that gnome will create and use an xml based registry similar to windows for some devices, kde takes this even further.

in windows......: 
 a folder is a folder is a folder is a file 
 a file is a file is a file is a file is a file 
 devices are listed in the registry or some other esoteric place that requires re-compiling each time new stuff is created...

So when you choose where to "mount" the drive(array or volume) what you are doing is provifing a "wormhole from the first drive to the drive in question. obviusly you cant physically merge the to drives together and neither are you doinf this with the mounting process....rather it is a gateway of sorts to that device.


hope i didnt end up confusing you more. proly did though...../cry /dance

---

### Post by PrismaticKen on 2007-02-15
So....what if I don't have an administrator tab in any of my menus?

I've also tried logging in as root...which doesn't work (don't worry, i configured it with a password using the user manager)  it says the "system administrator can not login from this screen"

So I just don't seem to have the stuff you're talking about...

you are refering to Xubuntu (streamlined server Ubuntu distro)....right?

I'd like to stay in Xubuntu for it's lower system requirements....but I suppose I could deal with regular Ubuntu if need be....but I'm not seeing why...Xubuntu.....a strictly server OS wouldn't have something as basic and...totally necessary to server function as a Disk manager....that's nuts.

---

### Post by PrismaticKen on 2007-02-15
*this message intentionally left blank* (couldn't figure out how to delete posts...can't seem to find a delete button anywhere)

---

