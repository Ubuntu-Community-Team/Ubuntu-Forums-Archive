---
title: "OOPS!!! can NOT access XP"
date: 2006-03-02
forum: Desktop Environments
---

### Post by kamicota on 2006-03-02
Hi All

Can anyone help me here PLEASE--->>>

Just installed Ubuntu on desktop and can NOT access my Windows XP partitions in Nautilus

Have searched som of the How to's etc but no luck

Cheers for Years

Colin

---

### Post by kaamos on 2006-03-02
Try System->Administration->Disks and click "browse".

Also look here: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by kamicota on 2006-03-02
Thanks

And BOY that was quick 

Will need to digest what you just sdent as I have been a point & Click with PCLos:cool: 

Cheers for years

Colin

---

### Post by kamicota on 2006-03-02
Righty Ho

We NOW have the Windows hard Drive on the desktop :D :cool: BUT-->>>

I have C, D, E, and F partitions in XP and that is "C" on the desktop

So looks like WE need the commands to mount the other partitions:-? 

So if I could be pointed there I would be GRATEFUL

and If I am a little tardy in replying a FRIEND NEEDS to go four OUR OWN CUP of UBUNTU Coffee :D :p 

Cheers for Years

Colin

---

### Post by Shikai on 2006-03-02
System > Administration > Disks

Select the harddrive, and click the Partitions tab. This will show all the partitions for the selected disk. Then repeat the steps you used to get your "C" drive mounted, but substitute the correct /dev/hdXY for each partition.

If you want to automount them at boot, there are posts here already about editting your /etc/fstab, so just do a search.

---

### Post by kamicota on 2006-03-02
Righty Ho Shikai

another OOPS!!!--->>>

All desktop Windows iocons are of the same C drive partition

Here I what I put into Gedit--->>>

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda7       /media/windows  vfat    iocharset=utf8,umask=000   0       0
Where in the HECK :confused: did I go wrong

Cheers for Years

Colin :o

---

### Post by Ramses de Norre on 2006-03-02
You need a different mount point for each partition, so make a directory for each partition (sudo mkdir /media/dir_name) and put these in your fstab.

---

### Post by kamicota on 2006-03-02
Heck You Lost me Ramses 

As to how to do this -->>>sudo mkdir /media/dir_name

Do I put - /dev/hda5 6 & 7 in for Directory name ???

Cheers for Years

Colin :confused: BUT :D

---

### Post by carlosqueso on 2006-03-02
Open a terminal (go to Applications -> Accesories -> Terminal) and type ```
sudo mkdir /media/hda5
sudo mkdir /media/hda6
sudo mkdir /media/hda7
``` and then edit your fstab file (I see you know how to do that) and change the /media/windows to match the directories you created.

---

### Post by aysiu on 2006-03-02
[QUOTE=kamicota]Heck You Lost me Ramses 

As to how to do this -->>>sudo mkdir /media/dir_name

Do I put - /dev/hda5 6 & 7 in for Directory name ???

Cheers for Years

Colin :confused: BUT :D[/QUOTE] When you mount a partition, you're essentially telling Ubuntu, "I want this partition to show up when I click on this folder."

In your posted /etc/fstab, you're telling Ubuntu, "I want this partition and that partition and that partition and that partition to all show up in /media/windows."

Each partition needs its own folder.

So you create a folder for each one, and your /etc/fstab should reflect that change. The folder name could be anything. You could do ```
sudo mkdir /i_hate_brown_bunny
``` You could mount /dev/hda6 there. You could mount /dev/hda7 at /ubuntu_sucks if you made a /ubuntu_sucks directory.

The *name* of the folder doesn't matter. Only these things matter:

1. There has to be a folder in order for a partition to be mounted.
2. Each partition needs its own unique folder--nothing else can be mounted at that folder, including another partition.
3. You must create the folder *and* associate the partition with that folder in your /etc/fstab

---

### Post by kamicota on 2006-03-02
Right Ho Calosqueue

Hope WE did this right here is the gedit

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /media/hda5  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/hda6 vfat    iocharset=utf8,umask=000   0       0
/dev/hda7       /media/hda7  vfat    iocharset=utf8,umask=000   0       0

And I HOPE all can bear with me as this is TOTALLY NEW to me

Cheers for Years

Colin:confused:

---

### Post by kamicota on 2006-03-02
:p WE are STILL in the OOPS mode though

As Desktop isons are Winows Windows  3 &4
and
The folders created in  the "Home Browser" show up but are empty  

So where too from here hopefully NOT back to PClos on both Laptop and Desktop

Colin a LITTLE :confused: and :mrgreen:

---

### Post by carlosqueso on 2006-03-02
there's another step...you must now open up a terminal and type ```
sudo mount -a
``` and it should work.  If it doesn't (which is possible), try restarting and it should work.

---

