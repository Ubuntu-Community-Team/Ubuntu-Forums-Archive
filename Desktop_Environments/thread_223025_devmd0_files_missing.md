---
title: "/dev/md0 files missing"
date: 2006-07-25
forum: Desktop Environments
---

### Post by machs_fuel42 on 2006-07-25
i'm having some troubles getting soft raid installed with dappper desktop install.  

I was following this guys guide
[http://www.mythtv.org/wiki/index.php/LVM_on_RAID](http://www.mythtv.org/wiki/index.php/LVM_on_RAID)

to get raid 5 set up on my box.  Everything was going well, array was rebuilding, about 50 % done when i had to restart.  
when ubuntu came back up, i had nasty error that halted boot

*** glibc dectected *** double free or corruption (!prev): 0x080634c ***

this occured right after LVM and then EVMS got loaded up.  i tryed restore mode with out any luck either.

I booted back to my w2k install ( eech. its so..... squishy) and did some reading of the forums, it seems that the glibc error is related to EVMS.  i managed to get ubuntu to a login screen by rythmically pounding on ctrl-c during linux boot.  i then apt-get removed evms and everything associated with it and rebooted.   gloriously dapper booted up fine.

However, i'd still like to get that raid array working, and it seems that i've no longed got any md* devices in /dev.  this is a problem.

I thought that perhaps EVMS, ubuntu-base, and ubuntu-standard packages that were removed might be needed, so i risked reinstalling them with add/remove.  Everything boots fine now, but stll no md devices.

i've looked at lsmod, and found that md_mod.o is there... i'm kind out of ideas on how to fix things at this point.

any help or direction would be great,:confused: 

hardware details

asus a7v8x
athlon 2800
promise ata 100 pci card
3 x 320 gig seagate drives

ubuntu dapper drake lts 6.06-i386

---

### Post by Xenolard on 2006-07-28
Same problem :(

---

### Post by machs_fuel42 on 2006-07-28
you sense of timing is impeccable...i managed to partially sort out this issue last night.

after a little more searching i found a post on the forums with a similar MO.  It seems that mdadm.conf is partially responsible for creating your md devices in dev.

[http://ubuntuforums.org/showthread.php?t=42087]("http://ubuntuforums.org/showthread.php?t=42087")

i changed my mdadm.conf around and rebooted, my array showed up fine, but evms failed on boot.  I took evms out with apt-get (good riddance) and a used mdadm -A -s to start rebuilding, i left it over night.  This morning i rebooted, and the array was there, and running fine. :)

I haven't tried putting LVM on there yet.. i think i might just format with XFS and be happy with that.

here is what my mdadm.conf file looks like

```
DEVICE /dev/hd[efh]*
PROGRAM /bin/echo
MAILADDR machs_fuel@nospam.com
ARRAY /dev/md0 level=raid5 num-devices=3 spares=1 UUID=4274771c:25037f23:4db837b4:86491cb8
    devices=/dev/hde,/dev/hdf,/dev/hdh auto=yes
```

---

