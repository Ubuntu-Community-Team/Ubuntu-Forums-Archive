---
title: "Very Slow File Copy"
date: 2007-04-15
forum: Desktop Environments
---

### Post by lank23 on 2007-04-15
Here is the issue;  If I copy a large file  1+ GB  from on folder to the next folder on the same SATA drive, I have not problems.

If I try to copy the large file(s) from one drive "SDA"  to the next drive "SDB"  Nautilus just sets there and finally copies some of the file(s) and then comes up with an error that the drive is read only.  The error only comes up after like and hour or so.

All the hard drives are connected to the Intel controller on my PB5 main board.

Here is my etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sda1
UUID=6fe28e70-2449-4bda-91e0-c85a2ddcff36 /               ext3    defaults,errors=remount-ro 0       1
#
# /dev/sda5
UUID=0ae85ebb-e7ed-470b-9d50-4bb43499049b none            swap    sw              0       0


#SATA 300 750GB drive in four parts of 174GB

/dev/sdb1       /media/sdb1     ext3  rw,nosuid,nodev 0 0
/dev/sdb2       /media/sdb2     ext3  rw,nosuid,nodev 0 0
/dev/sdb3       /media/sdb3     ext3  rw,nosuid,nodev 0 0
/dev/sdb4       /media/sdb4     ext3  rw,nosuid,nodev 0 0

#CDROM
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

And here is my lspci

```

00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation SATA Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
05:02.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

```

Thanks for the help.

Lank23

---

### Post by lank23 on 2007-04-16
I guess no one has any idea on a fix!

I did do this, moved the 750GB drive to different ports on the main board "Intel and JMicron", and I get the same results.  Changed the mounting to "default 0 2" and still same.  Try coping files using root and still same issue.

Any help would be great.

Lank23

---

### Post by lank23 on 2007-04-17
New news, I ran "chfs" on the drives and their was several errors.  So I fixed them all and now I can copy / move files to the drive, but it is still pretty slow.

Any idea?

Lank23

---

### Post by ComplexNumber on 2007-04-17
even though i haven't the magic wand, i thought i'd better chip in with what little i have to offer because i hate seeing people wanting help and not getting any response. 

you mentioned that you ran chfs and found that there are errors. that sounds about right for nautilus to react that way. it sounds as if there are still errors.

---

### Post by lank23 on 2007-04-17
There might still be errors, but how the errors are being generated has me clueless.  I only used nautilus to do file move / copy work so this leads me to think that somehow nautilus is creating the errors that "chfs" finds.

Note /media/sda1 is mount point of the first partition of my second sata drive.  Here is some speed test

If I copy a 1 GB file from say /media/sda1 to ~/home it takes about 23secs using nautilus
this gives me a 1024/23 = 44.5Mb/s

If I copy a 1 GB file from say ~/home to /media/sda1 it takes about 66 secs using nautilus
this gives me a 1024/66 = 15.5Mb/s

If I copy a 1 GB file from say ~/home to /temp it takes 63 secs using nautilus.
this gives me a 1024/63 = 16.25Mb/s

so if have both drives running at SATA 300 "300mB / sec" I should be getting faster speeds right?


Lank23

---

### Post by ComplexNumber on 2007-04-17
hjave you tried using the commandline to do the copying?  maybe that may give you some errors that may give some clue as to what the problem is.

---

### Post by lank23 on 2007-04-17
Did the same test in a terminal using "cp" command, and I get about 23 seconds on a copy to any location.  That means 1024MB/23 = 44.5MB/s

Also there was no errors show during any of the commands.

Lank23

---

### Post by lank23 on 2007-10-10
found the issue, one of my SATA cables would loose connection if it was bent just right.  So I replaced the cables with new ones and now the copying of files is really fast.

lank23

---

