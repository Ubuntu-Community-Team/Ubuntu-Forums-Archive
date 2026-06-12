---
title: "Error: no such device $UUID"
date: 2011-12-09
forum: Desktop Environments
---

### Post by Macamba on 2011-12-09
Hi,

I had some custom configured software in 11.04. So I was not eager to update to 11.10. Today I had an update of software. Something to do with energy saving applications. I was downloading something and went afk. After a while I came back to a customary black screen, moved my mouse to awake it, and nothing happened. So I rebooted my system, and got an:
"error: no such device: $UUID
grub rescue> _"
This meant I also had no access to my Windows partitions (*blush*).

I thought something might have gone wrong, lets try to get it right using my live CD. The first thing I noticed was I could not access the partitions on my hard drive. Next the Live CD asked if I wanted to upgrade. I started the upgrade as I thought I could always get the partitions working again during installation. But no luck. I had not enough space left on my boot partition. So now I'm downloading the Live CD for 11.10 (assuming my current Ubuntu partition is lost for ever) using my MacBook pro.

Anyway. Anyone know how I can get access to the partitions on my harddrive? I need to move my documents and mailbox to a save place (e.g. backup).

Macamba

---

### Post by Macamba on 2011-12-09
To complicate matters, if I try to boot the Live CD I burned on my MacBook Pro I get the same error. (*Gruble*) Must be the wrong format used while burning the CD. #-o

---

### Post by Macamba on 2011-12-09
The plot thickens. Using the Live CD 11.04 I did a "ls -l /dev/disk/by-label/" in a terminal window, and my hard drive was not recognised. I see my external HD, ready to receive the backup of Windows files" and the CD containing Live CD, but no HD. 

Is it time to "run in circles, scream and shout"? :confused:

---

### Post by mikejonesey on 2011-12-09
sounds like a hardware fault?
```
udevadm info -a -n sda | less
```

---

### Post by typhoon_tip on 2011-12-09
> **Macamba said:**
> The plot thickens. Using the Live CD 11.04 I did a "ls -l /dev/disk/by-label/" in a terminal window, and my hard drive was not recognised. I see my external HD, ready to receive the backup of Windows files" and the CD containing Live CD, but no HD. 

Is it time to "run in circles, scream and shout"? :confused:

Terribly sound like a dead HD to me... How old is (was...) it ?

---

### Post by Macamba on 2011-12-09
As old as my computer. 5 Years?

---

### Post by typhoon_tip on 2011-12-09
> **Macamba said:**
> As old as my computer. 5 Years?

Is not the MacBook, rite ? If not, then go into the BIOS and run an HD full diagnostic (it should have this utility).

On the bright side, if is a Desktop, might be a bad SATA cable (have that before many times).

---

### Post by Macamba on 2011-12-09
```
udevadm info -a -n sdb | less
```

I used sdb as sda is a second (older) HD I use.

I got things like 
```
looking at device '/devices/pci0000:00/00000:12.0/host2/target2:0:0/2:0?0?0?0/block/sdb':
   KERNEL=="sdb"
   SUBSYSTEM=="block"

``` 
etc.

I did the same in a separate terminal window for sda (the older HD) and got more or less the same output (differing for instance in the ATTR{model}'s: primary==SAMSUNG HD753LJ, secondary==Maxtor 6Y080L0

What next? Is this a sign my primary HD is alive?

---

### Post by mikejonesey on 2011-12-09
yep, this means udev can find your disk... the point of the above command is it shows all kernel modules loaded from the disk to the kernel... (path through pci/scsi...) do they all have modules loaded, can you manualy mount /dev/sdb1 /mnt?

---

### Post by Macamba on 2011-12-09
```
sudo mount /dev/sdb1 /mnt
mount: special device /dev/sdb1 does not exist

```

:confused:

---

### Post by Macamba on 2011-12-09
> **typhoon_tip said:**
> Is not the MacBook, rite ? If not, then go into the BIOS and run an HD full diagnostic (it should have this utility).

On the bright side, if is a Desktop, might be a bad SATA cable (have that before many times).

I'm in the CMOS Setup Utitliy in the IDE Configuration. My Primary IDE Master is my Atapi CDrom, my Primary IDE Slave is the Maxtor HD, probably sda (82 GB). My Third IDE Master is the Samsung I got with the computer, which is probably sdb (750 GB). 

Where does one find the HD full diagnostic you mentioned?

---

### Post by mikejonesey on 2011-12-09
check the disk via bios util as typhoon suggests, if this says it's ok then you need to set some extra udev rules and it will be found again, or perhaps you have just messed up the partition table? do you have a backup?

sudo fdisk /dev/sdb

then "p" to print the partition list...

there are also tools to guess your partition structure...

---

### Post by Macamba on 2011-12-11
Today I got it working again. Don't ask me why, without doing anything, except maybe giving my system a days rest, but today it booted as normal. 

:popcorn:

---

### Post by typhoon_tip on 2011-12-11
> **Macamba said:**
> Today I got it working again. Don't ask me why, without doing anything, except maybe giving my system a days rest, but today it booted as normal. 

:popcorn:

Don't rest on it, check SMART records with Disk Utility of Ubuntu, and see the health of the Hard Drive. Sound very like a SATA cable problem to me still.

---

### Post by mikejonesey on 2011-12-14
yes this sounds like a bad sata cable, more common in pc/servers...

---

