---
title: "[SOLVED] disk usage sprawling out of control"
date: 2008-06-18
forum: Desktop Environments
---

### Post by playalpha on 2008-06-18
(I posted this an hour ago in the wrong place, sorry for dupe)

I had Hardy installed on a 70G partition for about a month when it ran out of space (which I found out when I couldn't download a small picture.)

I did install a lot of software that I didn't really need, so I tried removing unneeded apps and old kernel-images with synaptic. Nautilus still showed 0 bytes available.

I then used gparted to increase the main partition to 110G with a separate 20G home partition. Once I completed that I rebooted some time later, but WHAMO! new 110G system partition is full (after copying old 70G to it with gparted).

It appears that every time I make more room, the system expands to fill the empty space.

Any help is appreciated...

---

### Post by Happy_Man on 2008-06-18
Try these commands, and then empty the Trash ```
sudo apt-get autoremove
sudo apt-get clean
```

---

### Post by playalpha on 2008-06-19
Thanks for the suggestion, but no joy...

autoclean removed 57M of files, but nautilus is still showing 0 bytes available. The drive keeps filling up but I haven't used it at all since repartitioning.

I really don't want to re-install since it's such a b^$%h to get Aptana (mostly) working on 64 bit. 

This reminds me of an art exhibit I read about in news of the weird which was made of replicating mice cells which died and turned into synthetic mouse-skin leather. They ended up growing out of control in the gallery and had to be disposed of...

---

### Post by p_quarles on 2008-06-19
I'd try to find out what's expanding so quickly. Open up your file manager, go to the root of the filesystem, and check on the size of each directory. Enter the largest directory, check on each subdirectory, and so forth. Narrowing it down to the largest subdirectory on the system, at least, may point to the application that is causing these problems.

---

### Post by Happy_Man on 2008-06-19
> **p_quarles said:**
> I'd try to find out what's expanding so quickly. Open up your file manager, go to the root of the filesystem, and check on the size of each directory. Enter the largest directory, check on each subdirectory, and so forth. Narrowing it down to the largest subdirectory on the system, at least, may point to the application that is causing these problems.
Or you could use Applications --> Accessories --> Disk Usage Analyzer.

---

### Post by beckols on 2008-06-19
Yea the disk usage analyzer would definitely be much faster :) It also has a very appealing graphical output, what more could you ask for??

---

### Post by playalpha on 2008-06-24
I may have found the problem using search (files over 50000K).

Automatic backup put about 40G in /var/backup.

That sounds reasonable (hmm) hit ctrl a, delete and back to work.

But, #$%^&! 0 bytes available. Maybe it needs to rescan the drives, can't hurt to restart...

Bam! (and not in the Emeril sense) zero bytes available.

Running beobab now, will post results
-C

---

### Post by playalpha on 2008-06-24
Okay, I am a Baffled Buffoon (sounds like an Ubuntu release gone wrong)

I unmounted all non-system external drives and partitions. 

"Scan Filesystem" in Disk Usage Analyzer reports the overall size of / to be 12.6GB with 100% usage.
"Scan Home" shows 4.5GB with 100% usage.

The partition is actually 110.78GB (per GParted).

Nautilus says I have 28.1MB free space.

I did not gain free space by deleting 40 GB of backups. They are not "there" anymore, but the system does not recognize the free space.

signed:confused:,

BB

---

### Post by mcduck on 2008-06-25
If you deleted the backup files with GUI tools they are not deleted, only moved to trash. Most likely the root's trash (inside /root) in this case.

You could also run "sudo fdisk -l" and "du -h" & post the outputs here..

By the way, if it really is some backup function that's eating your space, I'd recommend turning it off instead of removing the backup files. It will only do the same again and again..

Besides, having a backup on the same computer is pretty much the same as having no backup at all. I would never even do a backup to another disk in the same machine, failuing power source or something would still be able to wipe both original files and backups.. The only way to actually have useful backups is to burn them to disks or store them on some external drive that is only used for this purpose and is not connected to your computer but stored in some safe  place instead.

---

### Post by playalpha on 2008-06-25
Nautilus has a preference to enable "delete button bypasses trash" or something like that. I have that checked.

I turned off the backup (long story as to why it was pointed to the same drive, a temporary measure that I forgot about while I was messing around fstabbing a Win network drive), but needed the space back (40G) that it used, so I had to delete or move the backups off of the main disk.

I also ran ```
sudo rm -rf ~/.local/share/Trash/files/*
```
and the trash *looks* empty.

-any suggestions?

output of: 

fdsik -l 
du -h 

on next page...

---

### Post by playalpha on 2008-06-25
sudo fsdik -l

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          55       21841   175004077+   7  HPFS/NTFS
/dev/sda2           21842       38913   137130840    5  Extended
/dev/sda5           24322       38782   116157982+  83  Linux
/dev/sda6           38783       38913     1052226   82  Linux swap / Solaris
/dev/sda7           21842       24321    19920537   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

Disk /dev/sdg: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        7872     2015216    e  W95 FAT16 (LBA)

```

---

### Post by playalpha on 2008-06-25
du -h
```

ters
244K	./.wine/drive_c/Program Files/Mono-1.2.6/share/libgnomeprint/2.12.1
248K	./.wine/drive_c/Program Files/Mono-1.2.6/share/libgnomeprint
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/sgml/gconf
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/sgml
96K	./.wine/drive_c/Program Files/Mono-1.2.6/share/idl/bonobo-2.0
32K	./.wine/drive_c/Program Files/Mono-1.2.6/share/idl/bonobo-activation-2.0
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/idl/orbit-2.0
140K	./.wine/drive_c/Program Files/Mono-1.2.6/share/idl
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/pkgconfig
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gtkthemeselector/pixmaps
16K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gtkthemeselector
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/man/man5
52K	./.wine/drive_c/Program Files/Mono-1.2.6/share/man/man1
68K	./.wine/drive_c/Program Files/Mono-1.2.6/share/man
16K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gnome-2.0/ui
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gnome-2.0
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/MS-Windows/gtk-2.0
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/MS-Windows
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/Emacs/gtk-2.0-key
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/Emacs
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/Raleigh/gtk-2.0
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/Raleigh
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/Default/gtk-2.0-key
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes/Default
52K	./.wine/drive_c/Program Files/Mono-1.2.6/share/themes
268K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gtkhtml-3.8/icons
472K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gtkhtml-3.8
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/xml/libglade
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/xml
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/mime-info
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ta/LC_MESSAGES
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ta
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/gl/LC_MESSAGES
28K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/gl
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/pt/LC_MESSAGES
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/pt
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/et/LC_MESSAGES
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/et
108K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en@quot/LC_MESSAGES
112K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en@quot
168K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/vi/LC_MESSAGES
172K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/vi
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/eo/LC_MESSAGES
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/eo
168K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/es/LC_MESSAGES
172K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/es
116K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/de/LC_MESSAGES
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/de
84K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sl/LC_MESSAGES
88K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sl
116K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ja/LC_MESSAGES
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ja
16K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/nn/LC_MESSAGES
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/nn
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/hr/LC_MESSAGES
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/hr
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sk/LC_MESSAGES
124K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sk
88K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/zh_TW/LC_MESSAGES
92K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/zh_TW
28K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/id/LC_MESSAGES
32K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/id
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ms/LC_MESSAGES
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ms
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/nl/LC_MESSAGES
28K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/nl
116K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/it/LC_MESSAGES
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/it
52K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/be/LC_MESSAGES
56K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/be
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/fr/LC_MESSAGES
124K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/fr
116K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/pl/LC_MESSAGES
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/pl
112K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/zh_CN/LC_MESSAGES
116K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/zh_CN
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ga/LC_MESSAGES
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ga
32K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en_CA/LC_MESSAGES
36K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en_CA
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/cs/LC_MESSAGES
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/cs
56K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/da/LC_MESSAGES
60K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/da
108K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ro/LC_MESSAGES
112K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ro
132K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ko/LC_MESSAGES
136K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ko
128K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sv/LC_MESSAGES
132K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sv
112K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en@boldquot/LC_MESSAGES
116K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en@boldquot
28K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/fi/LC_MESSAGES
32K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/fi
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ca/LC_MESSAGES
124K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ca
52K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en_GB/LC_MESSAGES
56K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/en_GB
16K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/nb/LC_MESSAGES
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/nb
140K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ru/LC_MESSAGES
144K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/ru
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/no/LC_MESSAGES
24K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/no
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/hu/LC_MESSAGES
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/hu
44K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/pt_BR/LC_MESSAGES
48K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/pt_BR
120K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/tr/LC_MESSAGES
124K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/tr
136K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/uk/LC_MESSAGES
140K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/uk
16K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/el/LC_MESSAGES
20K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/el
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/az/LC_MESSAGES
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/az
124K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sr/LC_MESSAGES
128K	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale/sr
3.2M	./.wine/drive_c/Program Files/Mono-1.2.6/share/locale
52K	./.wine/drive_c/Program Files/Mono-1.2.6/share/jay
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/gettext
1.6M	./.wine/drive_c/Program Files/Mono-1.2.6/share/gapi-2.0
40K	./.wine/drive_c/Program Files/Mono-1.2.6/share/mono-1.0/mono/cil
44K	./.wine/drive_c/Program Files/Mono-1.2.6/share/mono-1.0/mono
48K	./.wine/drive_c/Program Files/Mono-1.2.6/share/mono-1.0
420K	./.wine/drive_c/Program Files/Mono-1.2.6/share/libgc-mono
68K	./.wine/drive_c/Program Files/Mono-1.2.6/share/aclocal
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/pixmaps
44K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/libiconv
16K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/sqlsharpgtk
28K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/gdiplus
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/packages/xsp
28K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/packages/monodoc-core
52K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/packages/IPCE
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/packages/ikvm
104K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc/packages
196K	./.wine/drive_c/Program Files/Mono-1.2.6/share/doc
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/share/mime/packages
12K	./.wine/drive_c/Program Files/Mono-1.2.6/share/mime
132K	./.wine/drive_c/Program Files/Mono-1.2.6/share/glade3/catalogs
332K	./.wine/drive_c/Program Files/Mono-1.2.6/share/glade3/pixmaps/22x22
332K	./.wine/drive_c/Program Files/Mono-1.2.6/share/glade3/pixmaps/16x16
680K	./.wine/drive_c/Program Files/Mono-1.2.6/share/glade3/pixmaps
816K	./.wine/drive_c/Program Files/Mono-1.2.6/share/glade3
42M	./.wine/drive_c/Program Files/Mono-1.2.6/share
112K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/GtkDemo/images
624K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/GtkDemo
108K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/rsvg
68K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/gconf
100K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/gnomevfs
328K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/valtest/.libs
24K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/valtest/.deps
648K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/valtest
116K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/test
60K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/pixmaps
136K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/opaquetest/.libs
40K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/opaquetest/generated
16K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/opaquetest/.deps
376K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0/opaquetest
2.6M	./.wine/drive_c/Program Files/Mono-1.2.6/samples/gtk-sharp-2.0
24K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/src/cui
60K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/src/bin/Debug
64K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/src/bin
36K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/src/gui
272K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/src
16K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/doc/CVS
16K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/doc/schemas/CVS
52K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/doc/schemas
76K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp/doc
384K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/prj2make-sharp
32K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/PEditGtk/PEditGtkSharp/bin
88K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/PEditGtk/PEditGtkSharp
100K	./.wine/drive_c/Program Files/Mono-1.2.6/samples/PEditGtk
3.1M	./.wine/drive_c/Program Files/Mono-1.2.6/samples
120K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/res/fonts
84K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/res/dtd
92K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/res/entityTables
44K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/res/html
580K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/res
12K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults/profile/chrome
12K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults/profile/US/chrome
20K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults/profile/US
40K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults/profile
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults/pref
16K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults/autoconfig
68K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/defaults
80K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/greprefs
2.4M	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/components
2.9M	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/chrome
36K	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner/plugins
16M	./.wine/drive_c/Program Files/Mono-1.2.6/xulrunner
1.4M	./.wine/drive_c/Program Files/Mono-1.2.6/include/gtk-2.0/gtk
68K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gtk-2.0/gdk-pixbuf
428K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gtk-2.0/gdk
1.9M	./.wine/drive_c/Program Files/Mono-1.2.6/include/gtk-2.0
524K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libxml
232K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgladeui-1.0/libgladeui
236K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgladeui-1.0
164K	./.wine/drive_c/Program Files/Mono-1.2.6/include/glib-2.0/gobject
400K	./.wine/drive_c/Program Files/Mono-1.2.6/include/glib-2.0/glib
580K	./.wine/drive_c/Program Files/Mono-1.2.6/include/glib-2.0
36K	./.wine/drive_c/Program Files/Mono-1.2.6/include/fontconfig
348K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeui-2.0/libgnomeui
356K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeui-2.0
48K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeprintui-2.2/libgnomeprintui
52K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeprintui-2.2
72K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gconf/2/gconf
76K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gconf/2
80K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gconf
32K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libglade-2.0/glade
36K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libglade-2.0
20K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gail-1.0/libgail-util
24K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gail-1.0
76K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnome-2.0/libgnome
80K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnome-2.0
184K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libart-2.0/libart_lgpl
188K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libart-2.0
96K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomecanvas-2.0/libgnomecanvas
100K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomecanvas-2.0
540K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libbonobo-2.0/bonobo
548K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libbonobo-2.0
76K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgtkhtml-3.8/gtkhtml
80K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgtkhtml-3.8
192K	./.wine/drive_c/Program Files/Mono-1.2.6/include/pango-1.0/pango
196K	./.wine/drive_c/Program Files/Mono-1.2.6/include/pango-1.0
24K	./.wine/drive_c/Program Files/Mono-1.2.6/include/librsvg-2/librsvg
28K	./.wine/drive_c/Program Files/Mono-1.2.6/include/librsvg-2
224K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gnome-vfs-2.0/libgnomevfs
228K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gnome-vfs-2.0
88K	./.wine/drive_c/Program Files/Mono-1.2.6/include/cairo
124K	./.wine/drive_c/Program Files/Mono-1.2.6/include/bonobo-activation-2.0/bonobo-activation
128K	./.wine/drive_c/Program Files/Mono-1.2.6/include/bonobo-activation-2.0
72K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gnome-vfs-module-2.0/libgnomevfs
76K	./.wine/drive_c/Program Files/Mono-1.2.6/include/gnome-vfs-module-2.0
176K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libbonoboui-2.0/bonobo
188K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libbonoboui-2.0
96K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeprint-2.2/libgnomeprint/private
196K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeprint-2.2/libgnomeprint
200K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgnomeprint-2.2
12K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgsf-1/gsf-win32
24K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgsf-1/gsf-gnome
192K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgsf-1/gsf
232K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libgsf-1
32K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libIDL-2.0/libIDL
36K	./.wine/drive_c/Program Files/Mono-1.2.6/include/libIDL-2.0
32K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono/cil
160K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono/metadata
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono/jit
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono/io-layer
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono/interpreter
52K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono/utils
272K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0/mono
276K	./.wine/drive_c/Program Files/Mono-1.2.6/include/mono-1.0
200K	./.wine/drive_c/Program Files/Mono-1.2.6/include/atk-1.0/atk
204K	./.wine/drive_c/Program Files/Mono-1.2.6/include/atk-1.0
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/orbit-idl
60K	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/ORBitservices
864K	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/orbit/orb-core
16K	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/orbit/util
104K	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/orbit/poa
112K	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/orbit/dynamic
1.1M	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0/orbit
1.2M	./.wine/drive_c/Program Files/Mono-1.2.6/include/orbit-2.0
7.9M	./.wine/drive_c/Program Files/Mono-1.2.6/include
16K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gtk-2.0
88K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/mono/1.0
104K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/mono/2.0
16K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/mono/mconfig
544K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/mono
24K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/fonts
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/2
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/applications/terminal
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/applications/help_viewer
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/applications/window_manager
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/applications/browser
36K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/applications
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/peripherals/mouse
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/peripherals/keyboard
20K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/peripherals
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/typing_break
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/accessibility/keyboard
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/accessibility/startup
20K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/accessibility
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/sound
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/background
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/file_views
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/interface
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/thumbnailers
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome/lockdown
136K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop/gnome
140K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/desktop
44K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/applications/terminal
60K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/applications/help_viewer
84K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/applications/window_manager
60K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/applications/browser
252K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/applications
192K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/peripherals/mouse
60K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/peripherals/keyboard
256K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/peripherals
72K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/typing_break
132K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/accessibility/keyboard
28K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/accessibility/startup
164K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/accessibility
36K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/sound
140K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/background
24K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/file-views
432K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/interface
32K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/thumbnailers
108K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/lockdown
1.5M	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop/gnome
1.5M	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas/desktop
1.5M	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults/schemas
1.7M	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/gconf.xml.defaults
1.5M	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf/schemas
3.1M	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gconf
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gnome-vfs-2.0/modules
12K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/gnome-vfs-2.0
8.0K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/bonobo-activation
44K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/sound/events
48K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/sound
12K	./.wine/drive_c/Program Files/Mono-1.2.6/etc/pango
3.8M	./.wine/drive_c/Program Files/Mono-1.2.6/etc
311M	./.wine/drive_c/Program Files/Mono-1.2.6
434M	./.wine/drive_c/Program Files
1.5G	./.wine/drive_c
1.5G	./.wine
12K	./.qt
8.0K	./.cddb/misc
12K	./.cddb
5.2M	./.thumbnails/normal
4.0K	./.thumbnails/large
5.2M	./.thumbnails
4.0K	./.gimp-2.4/gflare
4.0K	./.gimp-2.4/gimpressionist
4.0K	./.gimp-2.4/fonts
4.0K	./.gimp-2.4/tool-options
4.0K	./.gimp-2.4/levels
4.0K	./.gimp-2.4/patterns
4.0K	./.gimp-2.4/plug-ins
4.0K	./.gimp-2.4/curves
4.0K	./.gimp-2.4/themes
4.0K	./.gimp-2.4/brushes
4.0K	./.gimp-2.4/gradients
4.0K	./.gimp-2.4/fractalexplorer
4.0K	./.gimp-2.4/scripts
4.0K	./.gimp-2.4/palettes
4.0K	./.gimp-2.4/interpreters
4.0K	./.gimp-2.4/tmp
4.0K	./.gimp-2.4/templates
4.0K	./.gimp-2.4/environ
4.0K	./.gimp-2.4/modules
4.0K	./.gimp-2.4/gfig
468K	./.gimp-2.4
448K	./.fontconfig
1.6M	./ies4linux-2.99.0.1/winereg
52K	./ies4linux-2.99.0.1/ui/kommander
4.0K	./ies4linux-2.99.0.1/ui/.svn/prop-base
4.0K	./ies4linux-2.99.0.1/ui/.svn/props
4.0K	./ies4linux-2.99.0.1/ui/.svn/tmp/prop-base
4.0K	./ies4linux-2.99.0.1/ui/.svn/tmp/props
4.0K	./ies4linux-2.99.0.1/ui/.svn/tmp/text-base
16K	./ies4linux-2.99.0.1/ui/.svn/tmp
4.0K	./ies4linux-2.99.0.1/ui/.svn/text-base
40K	./ies4linux-2.99.0.1/ui/.svn
20K	./ies4linux-2.99.0.1/ui/pygtk
116K	./ies4linux-2.99.0.1/ui
128K	./ies4linux-2.99.0.1/lib
12K	./ies4linux-2.99.0.1/mac
176K	./ies4linux-2.99.0.1/lang
1.6M	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/winereg
52K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/kommander
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/prop-base
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/props
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp/prop-base
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp/props
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp/text-base
16K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/text-base
40K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn
20K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/pygtk
116K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui
128K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/lib
12K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/mac
176K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/lang
1.6M	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/winereg
52K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/kommander
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/prop-base
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/props
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp/prop-base
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp/props
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp/text-base
16K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/tmp
4.0K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn/text-base
40K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/.svn
20K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/pygtk
116K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui
128K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/lib
12K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/mac
176K	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/lang
2.0M	./ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1
4.3M	./ies4linux-2.99.0.1/ies4linux-2.99.0.1
6.6M	./ies4linux-2.99.0.1
12K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Handles
36K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Combo
36K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Buttons
24K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Others
44K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Scrollbars
60K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Toolbar
56K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Shadows
36K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Menu-Menubar
12K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Lines
20K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Frame-Gap
72K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Panel
16K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/ListHeaders
32K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Range
20K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/ProgressBar
32K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Spin
84K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Tabs
36K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Arrows
52K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Check-Radio
736K	./.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0
108K	./.themes/Mac4Lin_GTK_Aqua_v0.3/metacity-1
848K	./.themes/Mac4Lin_GTK_Aqua_v0.3
852K	./.themes
4.1G	.

```

---

### Post by RageAgainstThis on 2008-06-25
I cannot help, but I will let you know that the exact same thing happened to me after an upgrade from gutsy to hardy.  No matter what I deleted, files such as a distro iso, nautilus showed 0 bytes available.  Ended up reinstalling and crossing my fingers.  This was on a 160 WD drive.  I hope someone discovers why this is happening.

---

### Post by wdaniels on 2008-06-25
> **playalpha said:**
> I also ran ```
sudo rm -rf ~/.local/share/Trash/files/*
```
and the trash *looks* empty.

-any suggestions?

Yes, check root's trash folder also: /root/.local/share/trash/files

---

### Post by playalpha on 2008-06-26
> **wdaniels said:**
> Yes, check root's trash folder also: /root/.local/share/trash/files
ah, shucks! root's trash had 96 GB of crap in there and I succesfully deleted it AND the GUI knows all about it!

BUNTASTIC

As to the origin of the problem, I think it was from screwing aroung with "Simple Backup Config" and forgetting that it was running massive backups (including my Win user profile) back onto this partition.

Thanks for all the help muchacho/a s

---

### Post by mister_p_1998 on 2008-06-26
> **p_quarles said:**
> I'd try to find out what's expanding so quickly. Open up your file manager, go to the root of the filesystem, and check on the size of each directory. Enter the largest directory, check on each subdirectory, and so forth. Narrowing it down to the largest subdirectory on the system, at least, may point to the application that is causing these problems.

even better.. Id install Baobab, it will show your space useage in a trice. (Its in the Repos)

---

