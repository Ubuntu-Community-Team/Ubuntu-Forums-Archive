---
title: "How to install Quake Arena Ubuntu 11.10"
date: 2011-12-16
forum: Gaming &amp; Leisure
---

### Post by SeaHawk22 on 2011-12-16
I have a copy of Quake Arena for Linux I would like to install..... I have heard that it comes with a windows version on the disk as well that can be installed on wine... I am getting no where with installing, I tried following one blog instructions but it led me to an error because I run 64 bit the install doesnt work.

---

### Post by WienerWuerstel on 2011-12-16
ioquake3 is your solution. First you need to install the [Engine]("http://ioquake3.org/files/1.36/installer/ioquake3-1.36-7.1.x86_64.run") and then you can install the actual Game Files with this [Installer]("http://ioquake3.org/files/1.36/data/ioquake3-q3a-1.32-9.run").

Note that the Quake 3 Arena Disc needs to be inserted and mounted when installing the Game Files.

---

### Post by SeaHawk22 on 2011-12-17
Thank you very much, I guess I am sort of a newb, how do i run the installer?

---

### Post by WienerWuerstel on 2011-12-17
Open the Terminal and go into the Directory where the .run Files is like that ```
cd /path/to/the/Installfile
``` (Off course you need to change the path to your ACTUAL Folder where the Installation File is)

When you are in the Folder via Terminal do a ```
chmod +x runfile.run
./runfile.run
```(And again replace runfile with the ACTUAL Name of your .run file)

---

### Post by SeaHawk22 on 2011-12-17
Thank you, but I cannot for the life of me figure this thing out. Here is where I am getting stuck.

```
guhang@Guhang:~/ioquake3$ ./ioquake3
ioq3 1.36 linux-x86_64 Apr 12 2009
----- FS_Startup -----
Current search path:
/home/guhang/.q3a/baseq3
./baseq3

----------------------
0 files in pk3 files


pak0.pk3 is missing. Please copy it
from your legitimate Q3 CDROM.


Point Release files are missing. Please
re-install the 1.32 point release.


Also check that your Q3 executable is in
the correct place and that every file
in the baseq3 directory is present and readable.
You need to install Quake III Arena in order to play

```

---

### Post by rizzeh on 2011-12-19
copy all *.pk3 files in baseq3 folder from quake3 CD to /home/guhang/.q3a/baseq3 and try and run it again, post output here.

Alternatively go to [www.quakelive.com](www.quakelive.com) and play quake3 there. Majority of active quake players are there. Quake3Arena is pretty much dead now bar few crazy mods.

---

### Post by SeaHawk22 on 2011-12-24
EDIT

Never mind I got it to work! Thanks all! :)
Thanks again!

---

### Post by WienerWuerstel on 2011-12-24
Yes this will work and no, binary path doesn't mean the Quake 3 Disk.

This Installer is just for the ioquake3 Engine itself! Install this first and THEN install the actual Game with this [Installer]("http://ioquake3.org/files/1.36/data/ioquake3-q3a-1.32-9.run"). The Second Installer will install all the needed Game Files from the Quake 3 CD. 

I thought I made that clear in my previous posts.

---

