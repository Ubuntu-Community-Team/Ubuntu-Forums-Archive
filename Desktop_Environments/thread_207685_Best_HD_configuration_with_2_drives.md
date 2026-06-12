---
title: "Best HD configuration with 2 drives"
date: 2006-07-02
forum: Desktop Environments
---

### Post by mmcmonster on 2006-07-02
I am getting a new system with 2 SATA 250 GB drives.  The vast majority of this space will be for Ubuntu.  I plan on keeping maybe 10GB for MS Windows.

I was wondering what a good HD configuration would be.

My goal is to use most of this disk space as a combination backup for other computers on the (home) network and maybe to serve out music and other files to those computers.

I would guess I would like the vast majority of the space to be mounted as /home, but I can deal with multiple mount points if necessary. (I will be the only user logging into the system).

Any pointers to creating RAID arrays using multiple partitions on 2 drives?  Is it worth it?  What about simple GUI configuration for logical volume management?

---

### Post by karlsson88 on 2006-07-02
what about you do 25 GB for ubuntu (ext3), 250 GB as "fileserver" (FAT32), and i don't know how much space you need for the "backup-thing" and then the rest as "/home". or someting.

---

### Post by NiN on 2006-07-02
I'd suggest the following:
/dev/sda1            10GB   Windows
/dev/sda5            512MB/1G swap (just in case)
/dev/sda6            30GB   Ubuntu (ext3)

the rest with ext3 as /home and your data storage. (fat is crap for drives with that capacity)
look ah [http://www.fs-driver.org/](http://www.fs-driver.org/) for an ext2 driver for windows.

---

### Post by jgcamp99 on 2006-07-02
You'll need way more than 10 GB for MS Windows. I can already see you hitting a wall on that one and with 2 250 GBers (just like those that have hit the wall on a 10 GB Ubuntu install, I'm having so much fun with Ubuntu, in a month 18.* GB has about 9.2 GB free), why/don't be so stingy ?, let the OS's have a lot of real estate to breathe, while they don't downright play with each other, MS is very selfish and doesn't play well with others. Ubuntu, 20-25 GB is a minimium with that much total storage available. As for Fat32, I wouldn't at all for internal drives. So what format for the rest is determined by which is your primary OS. If primary (and this would lean towards rarely ever using Windows) is Ubuntu, leave 20-30 GB for Windows, You can always read NTFS to write to Linux for intercompatibility, just don't go read/write Linux to NTFS just yet.

I have the luxury and would recommend it to others, of a small 2.5 external notebook hdd that I use for fat32, it's something you can put together thru pricewatch relatively cheap, this and a 1 GB memory stick transfer files I want to share Linux to Windows. I've found fat32, to become corrupt more easily than ntfs and this is when a hdd starts to fail. I'd just assume keeping anything off fat32 for the long haul. But if you'll use the fat32 as a temporary landing zone in between Windows/Linux and vice versa, you'll have to determine the largest files and treat that fat32 as a hdd cache so to speak.

---

### Post by mmcmonster on 2006-07-02
Thanks for the replies.  I guess software RAID isn't for me.  Maybe in a future system if I build one with 4 drives or more.  I am primarily using the system as a backup for files found on other systems, so if there is a drive failure, I shouldn't really be losing much.

A volume management system such as [EVMS]("http://evms.sourceforge.net/") isn't for me, either, since I will likely want to access the drives even if I have to take them out and put them in other computers. (I've had to do that a number of times in the past).

I should have made it more clear: I don't plan on using Windows XP much at all.  The only thing I use it for is maybe making the final adjustments on a Powerpoint presentation, since there are differences in rendering between the Windows and OSX versions of Powerpoint, and maybe copying a few DVDs.

This is what I will end up with:
hda1 - ntfs - 25 GB - Windows XP
hda2 - ext3 - 9 GB - /
hda3 - swap - 1 GB
hda4 - ext3 - 215 GB - /home
hdb1 - ext3 - 250 GB - /usr/local/backup

On Windows XP I will have the [Ext2 IFS]("http://www.fs-driver.org/") installed, giving me full access to my ext3 partitions.

Is 9 GB for / too little?  My current Dapper installation is only using 5.2 GB, so I figure with "room to grow" 9 GB should be okay. :-)

---

### Post by NiN on 2006-07-02
[QUOTE=mmcmonster]Thanks for the replies.  I guess software RAID isn't for me.  Maybe in a future system if I build one with 4 drives or more.  I am primarily using the system as a backup for files found on other systems, so if there is a drive failure, I shouldn't really be losing much.

A volume management system such as [EVMS]("http://evms.sourceforge.net/") isn't for me, either, since I will likely want to access the drives even if I have to take them out and put them in other computers. (I've had to do that a number of times in the past).

I should have made it more clear: I don't plan on using Windows XP much at all.  The only thing I use it for is maybe making the final adjustments on a Powerpoint presentation, since there are differences in rendering between the Windows and OSX versions of Powerpoint, and maybe copying a few DVDs.

This is what I will end up with:
hda1 - ntfs - 25 GB - Windows XP
hda2 - ext3 - 9 GB - /
hda3 - swap - 1 GB
hda4 - ext3 - 215 GB - /home
hdb1 - ext3 - 250 GB - /usr/local/backup

On Windows XP I will have the [Ext2 IFS]("http://www.fs-driver.org/") installed, giving me full access to my ext3 partitions.

Is 9 GB for / too little?  My current Dapper installation is only using 5.2 GB, so I figure with "room to grow" 9 GB should be okay. :-)[/QUOTE]

you should link /tmp and /var/tmp to one of the bigger partitions if you want to do something that requires more space (working with dvd) or you won't have temporary space.
The rest sounds reasonable. (P.s. I forgot to mention: fs-driver mounts ext3 as ext2... so always shut down windows properly, or you will have a filesystem check every linux boot.

---

### Post by mmcmonster on 2006-07-02
Thanks!  I never thought about /tmp and /var/tmp.  Good to know.  Maybe that's why I have trouble ripping DVDs?  I'll have to try it again. :-)

---

### Post by mmcmonster on 2006-07-04
By the way, for those that do move /tmp and /var/tmp to another drive, remember to make the directories "sticky" (chmod +t tmp), and remember to reboot to complete the process.

I don't know why, but after I made the change I could not launch another terminal window until I did a reboot.  Possibly there was an open file handle pointing to a file in /tmp that didn't like the underlying file being moved to another partition. :oops:

Also, on systems with multiple users, /tmp and /var/tmp should be on a separate partition from the rest of the files.  That is because, since these are world-writeable, a malicious application (or user) can fill up whatever partition contains these directories.

---

### Post by mmcmonster on 2006-08-06
For those of whome who want to move /tmp and /var/tmp, a good place to move them is /home, since that is likely to be your largest partition.  Of course, if you may have malicious users on your system, both /tmp and /var/tmp should go to a small separate partition so that /home doesn't get filled.

```

sudo mkdir /home/.tmp /home/.vartmp
sudo chmod a+rwxt /home/.tmp /home/.vartmp
sudo mv /tmp/* /home/.tmp
sudo rmdir /tmp
sudo ln -s /home/.tmp /tmp
sudo mv /var/tmp/* /home/.vartmp/
sudo rmdir /var/tmp
sudo ln -s /home/.vartmp /var/tmp

```

---

### Post by liquideath on 2006-08-06
I find that 10 GB is enough for WinXP, unless you plan on installing games, Adobe products, or Visual Studio on that partition. I typically install that stuff on a larger separate partition, along with files, music, etc.

---

