---
title: "winxp on to physical device by vmware"
date: 2006-01-17
forum: Desktop Environments
---

### Post by bouncer070 on 2006-01-17
I've been trying to install windows xp on to a physical device through vmware 5.5.1.  The problem is i can not get passed the error "the specified device is not a valid physical disk device."  I'm not really sure what this means, as there is no information about this on vmwares website, manual, help pages, install guide, OR troubleshooting.  ubuntu is located on /dev/hda2 and I was trying to install onto /dev/hda1 (windows needs to be on the first partition if i ever plan on dual booting in the future).  After recieving the error i tried installing onto /dev/hda3 and got the same error.  I then treid a different hard drive /dev/hdb, and still the same.   I was wondering if anyone has solved this problem and if maybe its something wrong in the /etc/fstab?  I don't think its file permissions related, b/c i am in teh group "disk" and i've performed all these steps as root.  I've come to two possiblities, 1 is that i have something setup wrong in ubuntu, or 2 there is a "bug" in vmware.

I hope someone can help me this is driving me insane :( 

Thanks - ben

I have pasted a short clip of the vmware log. 

Jan 17 02:40:07: vmui| Cmd /host2/#64e5467be59d1055/util/disk/cmd/##58/op/getDiskPartitions/ failed: The specified device is not a valid physical disk device
Jan 17 02:40:07: vmui| DISKLIB-DEVCRL: LBA IDE disk 240121728 16383(238216)/16/63
Jan 17 02:40:07: vmui| DISKLIB-DEVCRL: Facts for /dev/hda: Cap=240121728 Phys C/H/S=16383/16/63 BIOS C/H/S=1024/255/63 Adap=IDE
Jan 17 02:40:07: vmui| DEVCREAT: PartitionTables : 3
Jan 17 02:40:07: vmui| DEVCREAT: At 0
Jan 17 02:40:07: vmui| DEVCREAT: At 125788950
Jan 17 02:40:07: vmui| DEVCREAT: At 237231855
Jan 17 02:40:15: vmui| VmdbVmCfg_UpdateFile: Could not load dictionary file /home/ben/vmware/Windows XP Professional 7/Windows XP Professional 7.vmx: Unable to get information about file "/home/ben/vmware/Windows XP Professional 7/Windows XP Professional 7.vmx": No such file or directory.
Jan 17 02:40:15: vmui| 
Jan 17 02:40:15: | VMHSWorkerMain started : thread id = 9561: Path: /host2/#64e5467be59d1055/util/disk/cmd/##6a/op/createDisk/
Jan 17 02:40:15: | DISKLIB-DEVCRL: LBA IDE disk 240121728 16383(238216)/16/63
Jan 17 02:40:15: | DISKLIB-DEVCRL: Facts for /dev/hda: Cap=240121728 Phys C/H/S=16383/16/63 BIOS C/H/S=1024/255/63 Adap=IDE
Jan 17 02:40:15: | DEVCREAT: PartitionTables : 3
Jan 17 02:40:15: | DEVCREAT: At 0
Jan 17 02:40:15: | DEVCREAT: At 125788950
Jan 17 02:40:15: | DEVCREAT: At 237231855
Jan 17 02:40:15: | DiskLibCreateParam: 0xb6ab3200
Jan 17 02:40:15: | ----------------------------
Jan 17 02:40:15: | AdapterType: buslogic
Jan 17 02:40:15: | CreateType: partitionedDevice
Jan 17 02:40:15: | DISKLIB-LIB   : Mismatched adapter type (2 vs 1)
Jan 17 02:40:15: | VMHS: failed to create disk '/home/ben/vmware/Windows XP Professional 7/Windows XP Professional 7.vmdk' : The specified device is not a valid physical disk device (20).
Jan 17 02:40:15: | Cmd /host2/#64e5467be59d1055/util/disk/cmd/##6a/op/createDisk/ failed: The specified device is not a valid physical disk device
Jan 17 02:40:15: | VMHSWorkerMain done : thread id = 9561
Jan 17 02:40:20: vmui| AIOMGR-S : stat o=4 r=8 w=0 i=6 br=194560 bw=0

---

### Post by qferret on 2006-01-17
1. Windows does not need to be on the first partition. You can point boot.ini to ANY partition.

2. What are you doing? If you're going to install Windows on the partition, install Windows on the partition. If you're going to run it under vmware, create the virtual drive for the OS in vmware.....:rolleyes: 

(Hope that didn't sound snippy...I'm just cornfused at what you're actually trying to accomplish)

---

### Post by bouncer070 on 2006-01-19
well when reading the vmware guide it says that it should be on the first partition, i was just following it step by step.... the reason that I don't run it through vmware is b/c i use a program called pro-e which does heavy rendering and it can't run through vmware with out taking my computer to a dead stop.  But i would like to be albe to just open windows in ubuntu so i can sinc my palm (b/c i have purchased palm programs that only work with windows so gnome-pilot is out) and other little things.  So i want to do a daul boot so i sinc my palm everyday (ideally through ubuntu) and be able to boot into windows to use pro-e (only once or twice a week)

Thanks - Ben

---

### Post by qferret on 2006-01-26
I've never tried setting up VMWare to use a physical drive than can actually be booted from outside of vmware.

Here's what I would do....

1. Do the dual boot setup.
2. Create a small VM with a virtual drive, allowing it access to the host file system.
3. Set the synch software in vmware to use the same paths as the software in your dual boot config.

"valid physical disk" error is gone, you get to synch your Palm in either environment, and if one Windows install gets hosed, you can still get into the other and try to fix it.

---

