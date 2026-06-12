---
title: "[SOLVED] Partition and File System Questions"
date: 2009-01-10
forum: General Help
---

### Post by Toribor on 2009-01-10
I'm in the process of reinstalling Ubuntu after a drive reformat and have a quick question about file organization.

I (will) dual boot Vista and Ubuntu on a 160gb mini SATA in my laptop. Last time I had around 20gb for Linux and the remainder of the drive was Vista and all my personal files. This worked okay except that I sometimes had to store files in my HOME directory (backgrounds, ect.) because if my NTFS partition didn't mount it couldn't access it until I force mounted it in the terminal.

Now, what I would like to do this time is have around a 40gb Vista partition, 20gb Linux partition, and use the remainder of the drive as a separate partition for personal files. What would be the best way of going about this? Should I mess with using that drive as HOME? What Filesystem should I use that will allow easy access from both Linux and Vista (Fat32? NTFS?)

Thanks a bunch!

---

### Post by dabang on 2009-01-10
OK, what I'd do is:
- create the first partition (sda1) as NTFS with Vista installer and install Vista
- start Ubuntu installer, create second partition (sda2) with ext3 for "/" (this will include your home directory)
- within Ubuntu installer create third partition (sda3) for swap and fourth partition (sda4 if primary or sda5 if logical) with fat32 as a shared drive for Vista and Ubuntu (maybe as /media/data)
Your home directory has to be a Linux filesystem like ext3 and must not be fat32.

---

### Post by ju2wheels on 2009-01-10
> **dabang said:**
> OK, what I'd do is:
- create the first partition (sda1) as NTFS with Vista installer and install Vista
- start Ubuntu installer, create second partition (sda2) with ext3 for "/" (this will include your home directory)


Agree with that but not with last point.

//Installing Vista
- sda1 40gb NTFS   //For vista, install first (makes install a little easier)
- sda2 120gb NTFS  //Create this also for now when you install vista and change it later with Ubuntu installer.

Pop in Ubuntu cd, activate the reposotories, and install ntfs-progs. Then start the isntaller.

//Installing Ubuntu
- sda1 40gb NTFS  //Mount as /media/vista if you want access, do not format, do not change file system leave it the same.
- resize sda2 to (100 - (RAMx2))gb, leave as NTFS, mount as /media/data or other
- create sda3 10gb ext3 for Ubuntu mount as /
- create sda4 10gb ext3 for Home mount as /home
- create sda5 (RAMx2)gb swap

This way you have access to Vista, your share drive is NTFS (which allows you to store files over 4gb which FAT32 doesnt allow) and accessible by Vista and Ubuntu, and you have your Ubuntu data in a home partition in case you mess up the OS.

Note: Just be sure you upgrade to the latest version of ntfs-3g once you install Ubuntu to avoid any NTFS issues.

---

### Post by Toribor on 2009-01-12
Fantastic! Everything worked swimmingly. Now I'm dual booting the right way. (I had weird issues before the reformat. Thank you both!

---

