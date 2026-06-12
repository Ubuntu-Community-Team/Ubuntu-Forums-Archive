---
title: "Windows 98SE Is Fusturation to Install!!!"
date: 2009-04-07
forum: General Help
---

### Post by Hyper Tails on 2009-04-07
Hi I have an old pc next to me with no os and I tryed lots of distrbuctions of linux to install and using lots of cd's (No of which worked)
so I gave up and now i want to install windows 98se and Everytime i put the disc in it loads up fine and i select start setup and the drives stops and a bunch of error messenges show up as missing file or corrupted, so i tested the cd in virtual pc and it was fine, so it's not the disc itself but why is the old pc doing this? i made a boot disk and selected setup.exe (with the cd in and it says you need 734000 bytes or something to start setup ( It has 4 Freakin gigs of space!) so what's the problem with it

Could SOMEone Help me with This issue Please!!!:mad:

---

### Post by 3Miro on 2009-04-07
If no OS installs it is probably a driver/hardware issue. Most likely, a piece of the old hardware has gone bad and is now preventing you from using the computer.

I might not be the case of course. I once had an old computer that would install and run only Mandrake 8.x and 9.x, no 10.x.

Consider the date/year when the computer was build (I don't know if you have that kind of information), then try to find an old version of Linux from around that time. That would be my best guess. (I think there is a server that keeps track of very old distros and versions, try finding it with google)

---

### Post by kerry_s on 2009-04-07
sounds like bad cdrom drive.
can it be replaced?
what are the specs of this machine?
are you connected to the internet or can connect?

---

### Post by Hyper Tails on 2009-04-08
well i am able to install win 2000 and xp on it (they both work fine) but I don't know why it's not letting install 98 (the reason Why i got rid of xp and 2000 because they ran slowly on that pc)

---

### Post by jake1017 on 2009-04-08
If the PC is slow I would recommend using Window Server 2003. In my experience (many VM's and computers) Windows Server is much faster than XP.

OR

Continue using XP and turn off all effects.

I wouldn't continue using 98SE as it is a dead OS and very rarely supported.

---

### Post by mhgsys on 2009-04-08
Windows 98 supports the FAT16 and FAT32 file system, NOT NTFS.

 So make sure you got a partition formatted as fat16 or fat32, 

The FAT16 file system has a maximum of 2 gigabytes (GB) for each allocated space, or drive letter. For example, if you use the FAT16 file system and you have a 6-GB hard disk, you can have three drive letters (C, D, and E), each with 2 GB of allocated space.

The FAT32 file system supports drives up to 2 terabytes in size and stores files on smaller sections of the hard disk than does the FAT16 file system. This results in more free space on the hard disk. The FAT32 file system does not support drives that are smaller than 512 MB

Guess you can install 98 after making a fat partition

---

### Post by Hyper Tails on 2009-04-08
well i tried formating it to fat 32 and Now it workS!~!!
i'm now in the setup and rafter i it does something it shows a black retangle and frezzes the setup

any advice?

---

### Post by lisati on 2009-04-08
I have a machine that runs Win98SE: one thing I did the last time I reinstalled was to copy the complete Win98 directory to a directory on the C: drive and running setup from there. That way, if I install drivers or update something, I'm not prompted for the Windows CD if it's required.

---

### Post by mhgsys on 2009-04-09
@hyper tails

Are you trying to install it on a slave disk perhaps?

Windows 98 needs to be primary disk, first partition on install.
After install you can make it a slave disk if you want to, editing grub and using the map (hd) commands to boot it.

---

### Post by Hyper Tails on 2009-04-09
It's doing that and it's the only partition on the computer

---

### Post by mhgsys on 2009-04-10
hmz, 
Are you trying to run setup.exe on d:\ perhaps? instead of setup on d:\win98?

try 
```

a:\> d:

    *where d: is your CD-ROM drive letter.*

d:\> cd win98

d:\win98 > setup /ie

```

**The /ie flag tells Windows 98 not to make a new Startup Floppy during the installation** So if you want one, don't use the /ie command.

Also Maybe you best do it the way lisati suggested ,so you wont need the cd ever again. (except reinstall, if hd is been formatted)
 

Make a c:\windows\options\cabs directory and copy the files from the win98 directory on the CD-ROM to the cabs directory.

```

    a:\> c:

    c:>md windows

    c:>cd windows (or simply type cd followed by the F3 key)

    c:\windows>md options

    c:\windows>cd options

    c:\windows\options>md cabs

    c:\windows\options>cd cabs

    c:\windows\options\cabs>copy d:\win98\*.*

        Again: where d: is your CD-ROM drive.

```

then install win98 with:```


    c:\windows\options\cabs>setup /ie

```

---

