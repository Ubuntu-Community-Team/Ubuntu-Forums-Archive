---
title: "Problem with Dapper detecting dvdrw"
date: 2006-07-12
forum: Desktop Environments
---

### Post by beanlover on 2006-07-12
I'm not sure what's going on here.  When I first installed Dapper on my desktop system everything was detected and working correctly.  I've burned several dvds successfully (even after recent updates to the system where others have reported only being able to create coasters).

In DMESG it appears to be detecting the drive correctly (note line for "hdc" below)

...snip...
[17179576.588000] Probing IDE interface ide0...
[17179577.020000] hda: IC35L060AVV207-0, ATA DISK drive
[17179577.304000] hdb: Maxtor 4D080H4, ATA DISK drive
[17179577.364000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.400000] Probing IDE interface ide1...
[17179578.280000] hdc: DVD-RW IDE1004, ATAPI CD/DVD-ROM drive
[17179579.068000] hdd: LG CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
[17179579.072000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.104000] hda: max request size: 1024KiB
[17179579.124000] hda: 117187500 sectors (60000 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
[17179579.124000] hda: cache flushes supported
[17179579.128000]  hda: hda1 hda2 < hda5 >
[17179579.152000] hdb: max request size: 128KiB
[17179579.152000] hdb: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179579.152000] hdb: cache flushes not supported
[17179579.152000]  hdb: hdb1
[17179579.172000] hdc: ATAPI 47X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[17179579.172000] Uniform CD-ROM driver Revision: 3.20
[17179589.408000] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
...snip...

At the end of dmesg just after a reboot I get this as well:

...snip...
[17179679.948000] hdc: DMA timeout retry
[17179679.948000] hdc: timeout waiting for DMA
[17179685.152000] hdc: status timeout: status=0xd0 { Busy }
[17179685.152000] ide: failed opcode was: unknown
[17179685.152000] hdc: drive not ready for command
[17179685.200000] hdc: ATAPI reset complete
...end...


I had, at one point, followed directions on how to enable DMA for the dvd drive due to jittery video playback.  Seemed to do the trick at the time but has been spotty ever since.  I removed the changes to hdparm.conf but still no joy.

Every once in a blue moon, after a reboot, I'll have my DVD RW drive listed in the "computer" and I can use nautilus to burn files to dvds.  Eventually the system hangs and the next reboot brings me back to "normal" where it's not even recognized.

I can mount the drive to read dvds but not to write to them.  The system won't automatically ask me what to do with blank dvd-r discs like it should (except when all appears well...then it does).

I also have the nvidia proprietary driver installed...everything else is basically as installed.  The only other this is I do have Quicken 2005 Premier Home and Business running under wine but I can't imagine that causing an issue.

Any help would be appreciated.

Thanks,

B

---

### Post by Anduu on 2006-07-13
So you say sometimes it works and sometimes not?

Seems to me your drive may be almost toast.

---

### Post by beanlover on 2006-07-14
While I can't rule out hardware failure I doubt that's the culprit.  The drive itself is only about 2.5 years old and has worked flawlessly the entire time (under Windows 2000).

I made a discovery last night (I think).  If I reboot the PC with a cd in the dvd-rw it properly detects the drive and I can use it to burn dvds with and generally access it.  Gnome mounts the drive for me when I put in a blank dvdr or any other disc so that's a good thing.  I guess I'll just keep a cd in there for reboots...wish I didn't have to.

Does anyone know how I can cause hald to output debug messages?  I'm sure there is a way but I don't know where to put the commands so it will be active at boot time.  I suspect it's either hald or DBUS causing this issue...then again I could be WAY off.

B

---

### Post by beanlover on 2006-07-14
I can mount the hardware even when nautilus doesn't do the automounting thing so this isn't a direct hardware failure.

When I look at the drives in the System -> Administration -> Disks it lists all the supported features of the drive successfully.  It also correctly lists the model name and number of the drive.  I can also mount dvds and cds for this drive using the disk manager.

I haven't tried to write to a dvd from the commandline because I don't want to waste a dvdr and I don't have a dvd-rw.

Anyone have any other ideas?

The dvdrw is hdc and my cdrw is hdd.  There is no entry in fstab for hdd but from what I've read debian doesn't require this to be the case for the drive to work correctly.  Is there any advantage to adding hdd to fstab?  I've done this in the past but it didn't seem to help...maybe I did it incorrectly and screwed something up.

Here is the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660     user,noauto     0       0

---

