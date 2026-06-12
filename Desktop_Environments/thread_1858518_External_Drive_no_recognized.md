---
title: "External Drive no recognized"
date: 2011-10-12
forum: Desktop Environments
---

### Post by redenex on 2011-10-12
WD 500GB External Drive. Contains data.

It is not getting recognized in Ubuntu 11.10 nor Windows 7.

fdisk -lu 
It is not reflecting either.

I checked the Disk Utility Tool, it displays the external drive, but says it should be formatted.

Any help to recover the data?

Thank you.

---

### Post by WasMeHere on 2011-10-12
Hi redenex,

I will try to help you with some questions and tips.

- Can you guess why you cannot read from the drive?
- Have tried to use another USB connection and another computer?

Anyway your computer can see the drive, but not the partition. Run ```
sudo fdisk -lu
``` and post the result!

There are tools to recover files without having a proper heading of the partition (partition table and pointers to the files). One of these tools is Photorec. It was originally intended for recovery of photos on flash drives with destroyed file allocations tables, but now it has developed into a general tool to get back files, as long as the file data is not overwritten, so

Avoid writing anything to your disk!

I suggest that you browse the internet to find information and tutorials about Photorec and prepare carefully to get files back!

Good luck
Olle

---

### Post by redenex on 2011-10-17
I have two external drives (same model), only this one is not getting recognized. I have recently backed up data onto this drive.

```
root@HP-TouchSmart-TX2:/home/teddy# fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfabf51e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   164039714    81916433+   7  HPFS/NTFS/exFAT
/dev/sda3       164040702   625137344   230548321+   f  W95 Ext'd (LBA)
/dev/sda5       164040704   242163711    39061504   83  Linux
/dev/sda6       242165760   253882367     5858304   82  Linux swap / Solaris
/dev/sda7       253891323   356289569    51199123+   7  HPFS/NTFS/exFAT
/dev/sda8       356289633   458687879    51199123+   7  HPFS/NTFS/exFAT
/dev/sda9       458687943   520120439    30716248+   7  HPFS/NTFS/exFAT
/dev/sda10      520120503   625137344    52508421    7  HPFS/NTFS/exFAT

```

sda1 and sda2 are Windows7 partitions

sda7, sda8, sda9 and sda10 are partitions on my internal hard disk.


PS: I am unsure what that sda3 stands for, checking it again.

Well, unfortunately theis particular External Disk is not getting recognized yet :(

---

### Post by coffeecat on 2011-10-17
@redenex, it's not encouraging that it is not recognised in either Ubuntu or Windows. In Ubuntu, it would probably be seen as sdb, so it is not a good sign that it is not seen with fdisk. (By the way, sda3 is an extended partition which is a container for all your logical partitions, sda5 to sda10.)

When you power on the drive, do you hear the disc spinning up? Do you have another power supply you could try with the USB enclosure? Sometimes power supplies fail enough not to deliver sufficient current, but still show a light.

Plug the drive in, switch it on, open a terminal and post the output of this command:

```
dmesg | tail
```

---

### Post by Dale61 on 2011-10-17
I had a similar problem not so long ago.  Borrowed the nephews 2TB external drive, and it worked like a charm and 11.04 didn't hesitate in reading / accessing it.

Borrowed the BIL's 1.5TB drive, and neither my Ubuntu only laptop or my defacto's W7 laptop could see it.  I did some searching and found that a common problem was a dry connection between the internal usb connector and the HDD unit.  OK, so nothing can be done about it.

BIL called in a couple of weeks later and said he tried his external drive when he got home and his laptop couldn't read it.  He replaced the USB cable with the one that came with it, and voila, problem solved.  What he had done was take a generic USB cable and packed it in with the HDD and that USB cable was faulty.

Change cables and see what happens.

---

### Post by redenex on 2011-10-17
> **coffeecat said:**
> 

```
dmesg | tail
```

```
[   65.255748] Info fld=0x0
[   65.255750] sd 5:0:0:0: [sdc]  Add. Sense: Logical block address out of range
[   65.255754] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   65.255761] end_request: I/O error, dev sdc, sector 0
[   65.256857] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   65.256862] sd 5:0:0:0: [sdc]  Sense Key : Illegal Request [current] 
[   65.256865] Info fld=0x0
[   65.256867] sd 5:0:0:0: [sdc]  Add. Sense: Logical block address out of range
[   65.256871] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   65.256878] end_request: I/O error, dev sdc, sector 0

```

---

### Post by redenex on 2011-10-17
> **Dale61 said:**
> 
Change cables and see what happens.

No luck with that either.

---

### Post by coffeecat on 2011-10-17
> **redenex said:**
> ```
[   65.255748] Info fld=0x0
[   65.255750] sd 5:0:0:0: [sdc]  Add. Sense: Logical block address out of range
[   65.255754] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   65.255761] end_request: I/O error, dev sdc, sector 0
[   65.256857] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   65.256862] sd 5:0:0:0: [sdc]  Sense Key : Illegal Request [current] 
[   65.256865] Info fld=0x0
[   65.256867] sd 5:0:0:0: [sdc]  Add. Sense: Logical block address out of range
[   65.256871] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   65.256878] end_request: I/O error, dev sdc, sector 0

```

Your external drive is being seen as sdc and that "I/O error, dev sdc, sector 0" doesn't look good at all.

I can only suggest what I would do if that was my drive, which would be to remove the actual drive from the enclosure and hook it up directly to a motherboard SATA header (if using a desktop machine) or put it in another USB enclosure or use an eSATA connection. That way you would be able to exclude the possibility of failure in the WD enclosure firmware, wiring or power supply.

---

### Post by redenex on 2011-10-17
Thank you, I am on a laptop. This malfunctioning happened while I connected this to my wife's laptop (to get some backed up data) and suddenly Windows said the drive cannot be loaded. Since then, it is almost dead :)

Will see and "pray" what best I can do to get back the crucial data.

thanks again.

---

### Post by WasMeHere on 2011-10-17
> **coffeecat said:**
> ...
I can only suggest what I would do if that was my drive, which would be to remove the actual drive from the enclosure and hook it up directly to a motherboard SATA header (if using a desktop machine) or put it in another USB enclosure or use an eSATA connection. That way you would be able to exclude the possibility of failure in the WD enclosure firmware, wiring or power supply.

+1
A colleague of mine used this method with success. There is a fair chance that the drive itself is working, so good luck :-)

Olle

---

