---
title: "Keeping external drives at the same /dev/xxx??"
date: 2006-06-25
forum: Desktop Environments
---

### Post by autocrosser on 2006-06-25
Been looking thru all the threads for a method to keep my external drives at the same /dev/xxx--I just moved from PPC to 686 & the drive I formated before (under PPC/MacOSX-one partition-ext3-disklabel-mac) shows up on my desktop as "Linux" & the same in my upper taskbar drive mounter--The new formated drive (two partitions-ext3--disklabel--msdos)shows up as 18.6gb & 18.6gb(2).

I've made a rule in /etc/udev/rules.d to "bind" the two "new" partitions--
10-local.rules
BUS=="usb", SUBSYSTEM=="block", SYSFS{dev}=="8.17", SYSFS{size}=="39070017", SYSFS{start}=="63", SYSFS{stat}=="     662     2700      290     2320", NAME{all_partitions}=="Games"

BUS=="usb", SUBSYSTEM=="block", SYSFS{dev}=="8.18", SYSFS{size}=="39086145", SYSFS{start}=="39070080", SYSFS{stat}=="     377      420        1        8", NAME{all_partitions}=="Tunes"

But this seems to not work--I've had to add the partitions to my /etc/fstab which works "some" of the time--seems that udev won't assign the same ident to the USB devices all the time??

I have thought to reformat the new drive with a disklabel of "mac"--this will create a 3mb "front" before the main partition--I'm guessing this will "allow" naming the partition (and make it "stick"??)

Any ideas I haven't explored???

---

### Post by mlind on 2006-06-25
Could you post the udev information of your extenal usb drives?

You must find correct device from /sys/bus/usb (could be on /sys/block/devices too ?)

```

for i in /sys/bus/usb/devices/*; do udevinfo -a -p $i; done | less

```


My hdd (not external) is /sys/block/devices/sda. I view its info using
```

udevinfo -a -p /sys/block/sda | less

```


For reference, see [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by autocrosser on 2006-06-25
The current address for the Partitions are at sdb1 & sdb2 (has changed to sda & sdc depending what I have plugged in at boot-time)

sdb1 looks like

device '/sys/block/sdb/sdb1' has major:minor 8:17
  looking at class device '/sys/block/sdb/sdb1':
    KERNEL=="sdb1"
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:17"
    SYSFS{size}=="39070017"
    SYSFS{start}=="63"
    SYSFS{stat}=="     380      429       10       80"

sdb2 looks like 

device '/sys/block/sdb/sdb2' has major:minor 8:18
  looking at class device '/sys/block/sdb/sdb2':
    KERNEL=="sdb2"
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:18"
    SYSFS{size}=="39086145"
    SYSFS{start}=="39070080"
    SYSFS{stat}=="     380      429        6       48"

And sdb looks like

device '/sys/block/sdb' has major:minor 8:16
  looking at class device '/sys/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:16"
    SYSFS{range}=="16"
    SYSFS{removable}=="0"
    SYSFS{size}=="78165360"
    SYSFS{stat}=="      78      756     1450      664       13        3      128       16        0
656      680"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.2/usb4/4-3/4-3:1.0/host3/target3:0:0/3:0:0:0':
    BUS=="scsi"
    ID=="3:0:0:0"
    DRIVER=="sd"
    SYSFS{device_blocked}=="0"
    SYSFS{iocounterbits}=="32"
    SYSFS{iodone_cnt}=="0x60"
    SYSFS{ioerr_cnt}=="0x0"
    SYSFS{iorequest_cnt}=="0x60"
    SYSFS{max_sectors}=="240"
    SYSFS{model}=="A               "
    SYSFS{queue_depth}=="1"
    SYSFS{queue_type}=="none"
    SYSFS{rev}=="0000"
    SYSFS{scsi_level}=="3"
    SYSFS{state}=="running"
    SYSFS{timeout}=="30"


(info for sdb1 & 2 was obtained from--
udevinfo -a -p $(udevinfo -q path -n /dev/sdb2) 
udevinfo -a -p $(udevinfo -q path -n /dev/sdb1)

I see that the STAT numbers keep changing

---

### Post by mlind on 2006-06-25
How about rule
```

BUS=="scsi", KERNEL=="sd*", SYSFS{**model**}=="A", NAME="%k", SYMLINK+="my_hd%n"

```

or

```

BUS=="scsi", KERNEL=="sd*", SYSFS{**model**}=="A", NAME="my_harddrive"

```

or even
```

SUBSYSTEM=="block", SYSFS{**size**}=="78165360" NAME="%k", SYMLINK+="my_hd%n"

```


I guess you must restart udev too
```

sudo /etc/init.d/udev restart

```


/edit 
added size rule too

---

### Post by autocrosser on 2006-06-25
Well-I tried different variations on all of those & some I thought up--Nothing seems to work:???:--So I reformated the drive (again with two partitions-disc label as mac) & "forced" the issue with fstab:evil:--Desktop is now right--disc mounter still calls them 18.6gb & 18.6gb(2)--but at least I can point Banshee at "Tunes" & it "seems" to stay there----

---

