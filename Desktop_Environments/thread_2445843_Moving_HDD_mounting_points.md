---
title: "Moving HDD mounting points"
date: 2020-06-20
forum: Desktop Environments
---

### Post by rubberduck1968 on 2020-06-20
Hi all, hope we're all well.

Ever since I upgraded my machine and I installed a new M.2 drive as my OS drive for 20.04 the other SSD and two HDD's have been listed as external. 

[[IMG]https://i.postimg.cc/JG4v1qkn/Gnome-file-2020-06-20-18-02-03.png[/IMG]]("https://postimg.cc/JG4v1qkn")
I know I have to change the mounting points in /etc/fstab but not entirely certain what I have to change in the fstab file. 

[[IMG]https://i.postimg.cc/kRM1gJDZ/On-This-Computer-2020-06-20-18-03-09.png[/IMG]]("https://postimg.cc/kRM1gJDZ")

[[IMG]https://i.postimg.cc/5X5CnwsB/fstab-2020-06-20-18-00-57.png[/IMG]]("https://postimg.cc/5X5CnwsB")

Much appreciate some help here, although I have been running Linux 12 years now, I never had this issue before or know why this has installed this way.

Cheers.

---

### Post by CelticWarrior on 2020-06-20
Not an issue. It's normal and expected.

Any data partition is typically mounted under /media (or in your case /mnt because propbably you used Disks to make them mounted on boot). It isn't being listed as "external" but as "removable" or "dismountable". The system actually doesn't make such distinction between internal and external. A Linux OS can be installed in an external drive  and the system partitions won't show up as removable the exact same way they wouldn't in an internal drive. And any data partition is shown as removable regardless of it residing in a secondary internal drive or in an external one.

Yes, you can change the mount points, but why?

---

### Post by rubberduck1968 on 2020-06-20
Because their listed as [COLOR=#000000]removable and can formatted or ejected which they cannot. Just nice to move them to where should be listed under computer.

That, and despite mounting them in Gnome disks, I have to mount everytime I want to use them.[/COLOR]

---

### Post by oldfred on 2020-06-20
Mounts in /mnt do not show in Gnome, that is standard.
I do mount my data partition in /mnt/data, but then link the folders into /home so seen normally.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

What format are those partitions?
If mounting by UUID, the mounts should not change.

---

### Post by rubberduck1968 on 2020-06-20
Thank you for the replies,[URL="https://i.postimg.cc/ZKbxPvHP/fstab-2020-06-20-18-00-57.png"]

https://i.postimg.cc/ZKbxPvHP/fstab-2020-06-20-18-00-57.png[/URL]

The three drive I'm talk are list as UUID, see above image, but what I don't understand is why on this install has 20.04 listed them as externals and not internal drives? Despite mounting though Gnome disk after reboot to access them I have mount each drive to use them.

On my previous setup my drives where listed under Other Locations, On This Computer, listed below Computer home drive and always mounted.

---

### Post by Morbius1 on 2020-06-20
>  but what I don't understand is why on this install has 20.04 listed them as externals and not internal drives?
Because **Disks** does something stupid.

It asks the user: "Show in user interface ?"

A reasonably intelligent person would look at that as say: "Well, of course I do". But it doesn't disappear if you do not select it. You just have to go find it under /mnt or create a bookmark to it.

Anywhoo, remove x-gvfs-show and all the other x-gvfs's and it won't show up as external. Should you decide to follow that advice give your mount points some meaning:

/mnt/Files
/mnt/Photography
...

---

### Post by rubberduck1968 on 2020-06-20
Thank you, yes that removed the external drive reference out of files.

[HTML]/dev/disk/by-id/wwn-0x5000c500c10090ad /mnt/wwn-0x5000c500c10090ad auto nosuid,nodev,nofail-name=Photography 0 0[/HTML]

[HTML]/dev/disk/by-id/wwn-0x5002538e410ccef4-part2 /mnt/wwn-0x5002538e410ccef4-part2 auto nosuid,nodev,nofail-name=Files 0 0[/HTML]

[HTML]/dev/disk/by-id/wwn-0x5000cca375dac4f2 /mnt/wwn-0x5000cca375dac4f2 auto nosuid,nodev,nofail-name=Videos%20%26%20Movies 0 0[/HTML]

What do I need to add to last three lines to be able to see and mount these drives within 'On This Computer' below? 
[[IMG]https://i.postimg.cc/kRM1gJDZ/On-This-Computer-2020-06-20-18-03-09.png[/IMG]]("https://postimg.cc/kRM1gJDZ")

I tried adding [COLOR=#000000]/mnt/Files and [/COLOR][COLOR=#000000]/mnt/Photography but got the following in the terminal.[/COLOR]

sudo mount -a
mount: /mnt/wwn-0x5000c500c10090ad: wrong fs type, bad option, bad superblock on /dev/sdc, missing codepage or helper program, or other error.
mount: /mnt/wwn-0x5000cca375dac4f2: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error.

---

### Post by rubberduck1968 on 2020-06-21
> **Morbius1 said:**
> 

 You just have to go find it under /mnt or create a bookmark to it.


/mnt/Files
/mnt/Photography
...

Tried do this, this morning by creating bookmarks for these two drives but I seem to be missing GUID Partition Tables on those drives which the SSD has. How do you attach a GUID Partition Table?

---

### Post by Morbius1 on 2020-06-21
Please post the output of the following command:
```
sudo blkid -c /dev/null -o list
```

---

### Post by rubberduck1968 on 2020-06-21
> **Morbius1 said:**
> Please post the output of the following command:
```
sudo blkid -c /dev/null -o list
```

[[IMG]https://i.postimg.cc/nMZbMDwM/Screenshot-from-2020-06-21-13-19-53.png[/IMG]]("https://postimg.cc/nMZbMDwM")

click to enlarge.

---

### Post by Morbius1 on 2020-06-21
I would like to give you a specific example but I'm not going to do it from screenshot information.

[1] Unmount the Photography partition

[2] Create a mount point under /mnt:
```
 sudo mkdir /mnt/Photography
```

[3] Change this:
> /dev/disk/by-id/wwn-0x5000c500c10090ad /mnt/wwn-0x5000c500c10090ad auto nosuid,nodev,nofail-name=Photography 0 0

To this:
```
UUID=bunch-of-numbers /mnt/Photography ext4 defaults,nofail 0 2
```

[4] Remount with this command:
```
sudo mount -a
```

---

### Post by rubberduck1968 on 2020-06-21
Mounted but not displayed but it does mean I can bookmark the drive for access.

[[img]https://i.postimg.cc/cvKqjKmm/Screenshot-from-2020-06-21-14-40-59.png[/img]](https://postimg.cc/cvKqjKmm)

All I need to do now is repeat the process for the other two drives I take it?

---

### Post by Morbius1 on 2020-06-21
Unless you want folks to end up hating you it would be best you stop posting screen shots and start posting actual data.

I'm surprised mount -a didn't through you an error. You need to remove that "-show" you have after "nofail"

Anyhoo, yes just repeat the process for the other partitions. And do yourself a favor and don't try to reproduce "Videos & Movies" in the mount point. Do CamelBack instead: 
> /mnt/VideosMovies
All those spaces and special characters is very un-Linux.

---

### Post by rubberduck1968 on 2020-06-21
> **Morbius1 said:**
> Unless you want folks to end up hating you it would be best you stop posting screen shots and start posting actual data.

Why....? computer porn maybe :biggrin: OK, will do.

> **Morbius1 said:**
> And do yourself a favor and don't try to reproduce "Videos & Movies" in the mount point. Do CamelBack instead:  Yes, the terminal did swear at me! :D

I have removed all the '-show' and must thank you again.

[COLOR=#000000]Think we can list this question now [Solved] [/COLOR]

---

### Post by Morbius1 on 2020-06-21
> Why....? computer porn maybe :biggrin: OK, will do.
It makes it far easier for the responder to copy and paste parts of your output for a tailor made response if the data presented is in text. Can't do it from a screen shot.

---

### Post by rubberduck1968 on 2020-06-21
> **Morbius1 said:**
> It makes it far easier for the responder to copy and paste parts of your output for a tailor made response if the data presented is in text. Can't do it from a screen shot.

Oh sorry, I never thought of that. :oops:

---

### Post by rubberduck1968 on 2020-07-01
I owe everyone an apology. 

This idiot was reading the online manual this afternoon for my Gigabyte X570 motherboard and no I hadn't set something after all. 

[[IMG]https://i.postimg.cc/hz5W3WwX/AHCI.jpg[/IMG]]("https://postimg.cc/hz5W3WwX")

The SATA mode selector was set to 'AHCI' which lists drives listed as external. Change to 'RAID' and the following appears...

[[IMG]https://i.postimg.cc/sQtHhVq4/other-locations-2020-07-01-18-06-44.png[/IMG]]("https://postimg.cc/sQtHhVq4")

Sorry people.

[COLOR=#272A34][FONT=&amp]To add, this is very strange as my other PC also running a Ryzen-Gigabyte setup with a 120 GB SSD plus 1TB HDD but no M.2 drive, if you set BIOS to RAID the PC will not boot into Linux?![/FONT][/COLOR]

---

