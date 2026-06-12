---
title: "Sharing NTFS partitions"
date: 2011-02-08
forum: Desktop Environments
---

### Post by thenovelist on 2011-02-08
I am trying to get my head around sharing the NTFS drives.  I have a dual boot with Win7 64bit 
```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```
I had gotten this far though.
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x616597e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       52218   419441053+   7  HPFS/NTFS
/dev/sda2           52219      121601   557318947+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e1af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29165   234259456   83  Linux
/dev/sdb2           29165       30402     9936897    5  Extended
/dev/sdb5           29165       30402     9936896   82  Linux swap / Solaris
omitting empty partition (5)

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6736718d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1           21283       60801   317436367+   f  W95 Ext'd (LBA)
/dev/sdg2               1       21282   170945536    7  HPFS/NTFS
/dev/sdg5           21283       60801   317436336    7  HPFS/NTFS

Partition table entries are not in disk order

```

But I want to be able to write my novel from both OS's and be able to work on my images with both OS's.  What then is my next step?
Thanks

---

### Post by coffeecat on 2011-02-08
Traditional advice would be to add entries to /etc/fstab so that whichever NTFS partitions you want to access from Ubuntu would be mounted on bootup. But that isn't necessary, since automounting is so good and easy with recent versions of Ubuntu.

Have a look in the Places menu. All your four NTFS partitions will be listed there, but unmounted. I can't say how they will be identified - it depends whether they have partition labels or not. If labelled, you will see the labels. If not, the partition size. Simply click on the one you want to open and a file browser will open.

Or - open a Nautilus (file browser) window: home, Computer, it doesn't matter which. Make sure you have 'Places' selected in the left pane and ditto for above.

And you don't even have to pre-mount a partition from Nautilus or the main menu to be able to open a file. Say you want to work on a Word document. Open OpenOffice Writer, File Menu > Open. Then you'll see the partitions listed in the left pane under 'Places'. click on the one you want and it will be automounted and then you can navigate to the file you need and open it.

However, if you were wanting to set up symlinks in your home folder to the NTFS partitions, then you would need to have them mounted on bootup. Post back if you need any help with this.

---

