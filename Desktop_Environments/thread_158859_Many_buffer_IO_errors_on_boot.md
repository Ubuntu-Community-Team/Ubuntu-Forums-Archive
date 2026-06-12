---
title: "Many buffer I/O errors on boot"
date: 2006-04-11
forum: Desktop Environments
---

### Post by SteveHoffmanUK on 2006-04-11
During my Breezy boot I am getting lots (maybe 20+) of messages that read:
```
[9999999.999999] Buffer I/O error on device hdb5, logical block 999999
```

Is there a way that these errors can be fixed? My system eventually boots OK but these seem to slow things down a lot -- about 4min for a boot.

---

### Post by SteveHoffmanUK on 2006-04-12
Can anybody help me on this?

Please?

---

### Post by dcstar on 2006-04-13
[QUOTE=SteveHoffmanUK]Can anybody help me on this?

Please?[/QUOTE]
It looks like a error on that filesystem, you may want to check what hardware mode /dev/hdb is running under with:
```
sudo hdparm -Ii /dev/hdb
```
and then post the contents of your fstab file here.

---

### Post by SteveHoffmanUK on 2006-04-13
```
/dev/hdb:

 Model=Maxtor 6E040L0, FwRev=NAR61EA0, SerialNo=E1VCNPWE
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80293248
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode


ATA device, with non-removable media
        Model Number:       Maxtor 6E040L0
        Serial Number:      E1VCNPWE
        Firmware Revision:  NAR61EA0
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   80293248
        device size with M = 1024*1024:       39205 MBytes
        device size with M = 1000*1000:       41110 MBytes (41 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 1
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 0
        Advanced power management level: unknown setting (0x0000)
        Recommended acoustic management value: 192, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    NOP cmd
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    FLUSH CACHE EXT command
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    Automatic Acoustic Management feature set
                SET MAX security extension
                Advanced Power Management feature set
           *    DOWNLOAD MICROCODE cmd
           *    SMART self-test
           *    SMART error logging
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 1 determined by the jumper
Checksum: correct
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto 

```

What does this reveal? Newbie here.

---

### Post by Sef on 2006-04-13
> /dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1

You have problem with your root partition.  Not sure exactly how to fix it, so I 'll let someone else answer that.

---

### Post by xyz on 2006-07-07
Have you tried, in Recovery Mode and at the root prompt:
```
fsck....or e2fsck
```

Typing these in will give you various options, f.inst. the "-y" option which will answer 'yes' to the question 'Do you wnat to fix it?'
Don't use these on mounted hdX or ext!

---

### Post by xyz on 2006-07-07
You could also check this link out...it is a list of errors + explanation:
[http://www.tldp.org/FAQ/Linux-FAQ/error-messages.html#my-syslog-says-end-request](http://www.tldp.org/FAQ/Linux-FAQ/error-messages.html#my-syslog-says-end-request)

---

### Post by SteveHoffmanUK on 2006-07-07
Thanks for the replies. 

After failing to install either Ubuntu or Windows XP on the two internal hard disks, I concluded that they are clapped out and need replacing. 

So I took 'em out and replaced them with a single hard disk and installed Ubuntu, without a hitch and am now Windows-free. Whee!

I conclude that I was right about the disks -- they don't last forever, being electro-mechanical devices.

---

### Post by xyz on 2006-07-07
Glad you figured it out...I'm having big-time HD pbm and can't really afford replacement. If you care to take a look at it:
[http://www.ubuntuforums.org/showthread.php?t=206742](http://www.ubuntuforums.org/showthread.php?t=206742)

---

