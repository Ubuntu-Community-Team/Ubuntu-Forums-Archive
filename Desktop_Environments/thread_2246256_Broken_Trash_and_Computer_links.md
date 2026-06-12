---
title: "Broken Trash and Computer links"
date: 2014-09-29
forum: Desktop Environments
---

### Post by hidde2 on 2014-09-29
Hey,

I recently updated from 12.04 LTS to 14.04 LTS and n[COLOR=#000000]ow strangely I get an error when I try to open the Computer, Trash and Network locations.[/COLOR]
[COLOR=#000000]I will attach screenshots of the error messages.[/COLOR]

[ATTACH=CONFIG]256804[/ATTACH][ATTACH=CONFIG]256805[/ATTACH][ATTACH=CONFIG]256811[/ATTACH]

[COLOR=#000000]I can use the filemanager to browse to the corresponding locations ("/" and "~/.local/share/Trash/files")
[/COLOR]I don't know where to look for Network.
[COLOR=#000000]But I can't use the links under "Places"

However if I try to go to Computer from within the filemanager it works fine.
[/COLOR][ATTACH=CONFIG]256810[/ATTACH][COLOR=#000000]

Any idea what could cause this? :)[/COLOR]

---

### Post by Bashing-om on 2014-09-29
hidde2; Hello, again.

Let's clarify to the forum the DE in use here and if any symlinks have been (or should be) established:
```

echo $DESKTOP_SESSION
ls -al /etc
ls -al /home
ls -al /home/hidde
ls -ld .local/share/Trash

```
Do we have the config files under " usr/share/xsessions/ubuntu.desktop "

Speaking of symlinks, what is the partitioning on the system ?
```

sudo fdisk-lu
sudo parted -l

```

With that I think we can start poking about
[INDENT][INDENT]see what we can find[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-29
Hey Bashing-om,

I think I might have found a problem which might be related to this. I had some problems earlier echoing system variables. They all seem to come up empty. 
echo $DESKTOP_SESSION returns nothing either.

The DE should be gnome as far as I know

the /etc and /home/bever folders are both holding a lot of files/folders I'm not sure if I should post the results of them on the forum.

however the results for the other 3 commands are:
```

$ echo $DESKTOP_SESSION



$ ls -al /home
total 16
drwxr-xr-x  4 root      root  4096 Nov  7  2013 .
drwxr-xr-x 25 root      root  4096 Sep 26 19:54 ..
drwxr-xr-x 41 bever     bever 4096 Sep 29 19:13 bever
drwxr-xr-x  2 sambauser users 4096 Nov  7  2013 sambauser


$ ls -ld .local/share/Trash
drwx------ 5 bever bever 4096 May 30 10:16 .local/share/Trash

```

There is no file or folder called ubuntu.desktop in that location, however there is a file called gnome.desktop.

```

$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT


Disk /dev/mapper/TheBurrow--vg-root: 41.3 GB, 41292922880 bytes
255 heads, 63 sectors/track, 5020 cylinders, total 80650240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/TheBurrow--vg-root doesn't contain a valid partition table


Disk /dev/mapper/TheBurrow--vg-swap_1: 3703 MB, 3703570432 bytes
255 heads, 63 sectors/track, 450 cylinders, total 7233536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/TheBurrow--vg-swap_1 doesn't contain a valid partition table


Disk /dev/mapper/TheBurrow--vg-UserData: 74.1 GB, 74088185856 bytes
255 heads, 63 sectors/track, 9007 cylinders, total 144703488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/TheBurrow--vg-UserData doesn't contain a valid partition table
Note: sector size is 4096 (not 512)


Disk /dev/sdb: 3000.6 GB, 3000590401536 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566016 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0015b953

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256   732566015  2930263040    7  HPFS/NTFS/exFAT





$ sudo parted -l
Model: ATA WDC WD1200BEVS-2 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  200MB  199MB  fat32        EFI System Partition  boot
 2      200MB   456MB  256MB  ext2                               msftdata
 3      456MB   120GB  120GB                                     lvm




Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  3001GB  3001GB  primary




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/TheBurrow--vg-UserData: 74.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  74.1GB  74.1GB  ext3




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/TheBurrow--vg-root: 41.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  41.3GB  41.3GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/TheBurrow--vg-swap_1: 3704MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  3704MB  3704MB  linux-swap(v1)

```

I see some errors there, I guess those need to be resolved?

---

### Post by Bashing-om on 2014-09-29
hidde2; Well,

I do not see anything obvious to this time.
As to " I see some errors there, I guess those need to be resolved?" I do not think there is a problem because ->
> 
sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

I had the thought that might be the case -> parted -l !
For a more indepth look at GPT partitioning there is the 'gdisk' tool available in the repository.

Let's await others to chime in as I do not have any familiarity with the gnome desktop.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-30
It looks like I was right, my system seems to be missing all or most of it's environment variables. I have no clue what to to do next. I'm guessing there is no easy way to restore this. For now I'm just going to try and fix what I can fix and then get ready for a full reinstallation.

But first I will have a little look around to see if I can't fix those environment variables :p

---

### Post by hidde2 on 2014-09-30
I spoke too soon, some links were broken but they were broken because apache2 couldn't find the files because of name changes in an update.

That is all fixed and working now, so I'm back to the problem with the Trash, Computer and Network locations not working.

---

### Post by Bashing-om on 2014-09-30
hidde2; Hey, hey.

I can appreciate all the time and effort you are putting into saving this install. It is great things are working out.

As to the GUI situation - while I continue to seek guidance on gnome - 
What results:
```

sudo dpkg-reconfigure gdm

```

[INDENT][INDENT]a patch in time is worth ?
[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-10-01
When I run that it shows me the screen about multiple display managers installed.
Which is kind of odd since I checked and gdm is the only one installed, lightdm is actually not installed.

```

$ sudo dpkg-reconfigure gdm

[ATTACH=CONFIG]256849[/ATTACH][ATTACH=CONFIG]256850[/ATTACH]

$ sudo apt-get remove lightdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'lightdm' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```

---

### Post by Bashing-om on 2014-10-01
hidde2; Well ! - impolite explisative here -

At least we know a bit more;
Have you taken the hint and looked in " /etc/init.d " to see what DeskTops might be activated ?

And then there is the advisory:
> 
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

Let's take a look and see what is not upgraded:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##to deal with those 6 that are not installed.

```

We do make progress
[INDENT][INDENT][/INDENT][/INDENT]I am confident there will be an end

---

### Post by hidde2 on 2014-10-02
Hey!

I did look in "/etc/init.d", it doesn't hold any file called lightdm, it does have the gdm file.

those updates are new, but I will install them right away. Seems like I am getting new updates every day :p
"sudo apt-get upgrade" updated them just fine.

Maybe I should just give it what it wants, install lightdm, switch from gdm to lightdm and see if that works any better?
Might help since lightdm is ubuntu's default display manager..

Still strange that it thinks that lightdm is installed. I did find a config file for lightdm in "/usr/share/lightdm/lightdm.conf.d/", that folder holds one file: "50-unity-greeter.conf".

---

### Post by Bashing-om on 2014-10-02
hidde2; Welp ,.....

I am of the opinion that:
> 
Maybe I should just give it what it wants, install lightdm, switch from gdm to lightdm and see if that works any better?
Might help since lightdm is ubuntu's default display manager..

will but compound the problem.. I could be in error ! I think this is but a configuration issue to establish some GUI links, After all, the server by default has no GUI, this was added. If worst comes to worst, we could remove the GUI and then re-install it ! 

I am still trying to learn where those GUI/folder links are. As I have no access to a GDM desktop, I am having a tough go of it.


[INDENT][INDENT]it's a failure to communicate
[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-10-02
I will have a look around as well. Thanks for the effort.

---

