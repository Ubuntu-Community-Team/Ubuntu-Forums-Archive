---
title: "FSCK Fail"
date: 2009-01-18
forum: General Help
---

### Post by Gillette on 2009-01-18
I'm using Intrepid Ibex and every time I boot up the computer it runs FSCK and there is something that comes up in red FAIL everytime. It happens so fast I can't see what it is that failed. The computer boots up normally and operates normally. How can I find out what is failing and what can I do to get it fixed?

---

### Post by taurus on 2009-01-18
Do you have windows on your machine and did you happen to have an entry in /etc/fstab to have it mount upon boot?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by Gillette on 2009-01-18
I only have Ubuntu on this computer.

---

### Post by taurus on 2009-01-18
Let's have a quick look at your /etc/fstab then.

```
cat /etc/fstab
```

---

### Post by Gillette on 2009-01-18
Here are the results from that command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26e963f0-8b69-48f2-82df-2cbd5b7db913 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=66079641-59f6-496d-833c-7aed9b263233 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Gillette on 2009-01-19
I didn't see the Fail indication this morning when I booted up the computer. But the fsck still ran. Isn't it supposed to run every 20th time you boot up? How can I get it to stop running every time?

---

### Post by taurus on 2009-01-19
Have a look at tune2fs.  You can adjust the number of mounts after which the filesystem will be checked with the -c option.

```
man tune2fs
```

---

### Post by Gillette on 2009-01-19
So do you write it like this? tune2fs -c 20

---

### Post by taurus on 2009-01-19
You need to run it with root privilege and you have to include a partition/device.

```
sudo tune2fs -c 20 /dev/sda1
```

---

### Post by Gillette on 2009-01-19
I did that and restarted the computer. FSCK ran again but initially it announced it was running with the Ubuntu logo on the screen. I didn't see any fail indications but it does look like there is some sort of message that is where the fail normally occurs. Anyway to slow this down so one has time to read it?

---

### Post by taurus on 2009-01-19
If fsck keeps scanning /dev/sda1 each time you boot, I would start to worry about the health of the harddrive then.

---

### Post by Gillette on 2009-01-19
I restarted the computer again and FSCK ran again and the Fail message appeared this time. I think it has something to do with "Running DKMS" and something about NVIDIA.

---

### Post by RJARRRPCGP on 2009-01-19
I would worry about the health of your hardware. Also, are you overclocking?

---

### Post by Gillette on 2009-01-19
It is a really old computer. I don't overclock and wouldn't know how to if I wanted to.

---

### Post by taurus on 2009-01-19
What's the spec of your machine then?

---

### Post by Gillette on 2009-01-19
System monitor says for hardware:

Memory: 501.3 MiB
Processor: Pentium III (Coppermine)
Available disk space: 2.7 GiB

It has a 9 GB harddrive. Is there somewhere Ubuntu will tell me what make the harddrive is?

---

### Post by fjgaude on 2009-01-19
> It has a 9 GB harddrive. Is there somewhere Ubuntu will tell me what make the harddrive is?

Yes, several ways. Here's one:

```
sudo hdparm -i /dev/sd[n]
```

or whatever your hard drive's name is.

---

### Post by RJARRRPCGP on 2009-01-19
I would replace the HDD.

---

### Post by Gillette on 2009-01-19
Here are the resuls for the hdparm -i command:
 
Model=ST310212A                               , FwRev=3.39    , SerialNo=6EG0CKFR            
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=512kB, MaxMultSect=32, MultSect=?8?
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=19541088
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5

 * signifies the current active mode

---

### Post by Gillette on 2009-01-19
I don't have anything I'm worried about loosing on this computer. I just use it for email, internet, etc. I've got several "geriatric computers" as alternates if this one fails.

---

### Post by fjgaude on 2009-01-19
Well, you have a Seagate ST310212A...

---

### Post by Gillette on 2009-04-24
I upgraded to Jaunty yesterday and the message is gone. It does not seem to be a hard drive issue after all.

---

