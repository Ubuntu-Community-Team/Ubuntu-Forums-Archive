---
title: "Is there any way to &quot;repair&quot; an Ubuntu installation?"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Vcount on 2006-08-28
Like windows offers a "repair" this installation feature when you put in an installation disk.  

I have a Dapper 32 installation that was killed by accessing one internal drive from another, as described in this [tutorial](http://www.psychocats.net/ubuntu/mountlinux.html), and now I'm getting messages like "stale NFS locks" and "no settings could load" and it won't even load Gnome, so I can't usefully navigate any more.  Essentially, the installation is useless now on that drive.    

I've got many install disks.  What I would PREFER to do is "repair" that installation so that it will boot gnome again, because I put a lot of work into it getting wine to work the way I wanted and installing various programs.  

Is this possible?  Or am I going to have to lose everything program-wise on that drive and reformat and reinstall?

---

### Post by Shadyman on 2006-08-28
Ditto. I just nerfed my install by using usermod -G instead of usermod -Ga, and now I'm not a 'sudoer' anymore. So I can't add myself back in.](*,)

---

### Post by cptnapalm on 2006-08-28
Shadyman, all you need to do is to boot into the single user mode and then reapply that.  single user mode boots up as root.

NFS is the network filesystem...  hmm

Vcount, no GUI at all?

I'm not seeing anything on that page that should do anything bad at all.

could you post your /etc/fstab?  (just cat /etc/fstab > /home/yourusername/fstab.txt then cut and paste it here)

what cfdisk reports your hard drives are might be good too.

---

### Post by Vcount on 2006-08-28
Okay, here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb2       /storage         ext3   defaults       0        0


The first thing I tried to get my other drive working was taking out the "/dev/hdb2" line, that being the one I added.  Since doing that didn't help at all, I put it back in so I could at least salvage the data on that drive, if not the programs I installed on it.  

When I type "cfdisk", this is what comes up:

                      cfdisk 2.12r

                              Disk Drive: /dev/hda
                         Size: 656236544 bytes, 656 MB
               Heads: 255   Sectors per Track: 63   Cylinders: 79

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
                            Pri/Log   Free Space                         649.80











     [  Help  ]  [  New   ]  [ Print  ]  [  Quit  ]  [ Units  ]

That is my cd/dvd drive, with a cd in it, which is why I assume it says 649.80 MB of space.  I don't know what to do to get it to show another drive, so I could show you the output for hdb2.  When I type "cfdisk hdb2" it says fatal error, cannot open disk.

---

### Post by Vcount on 2006-08-28
Oh, and it does have a GUI.  I can see the mouse, and the items on my desktop (a cd when a cd is in the drive, a flash drive when it's plugged in) show up.  But there is no navigation menu, top or bottom, and no desktop background, and no way I can see to graphically navigate to anything I want to run.

---

