---
title: "grub error 17 : corrupt partition."
date: 2009-05-07
forum: General Help
---

### Post by Qtastic on 2009-05-07
I did search around in the forums and found some similar threads, but no possible solution for my specific problem. Hence the post.
 
On my brothers computer, the "root" partition is on sda1 and the home partition on sdb1.
After a normal shutdown, the pc wouldn't boot up again and gives error 17 while loading grub. (before the menu).
 
I booted with a live cd and sdb1 was mounted directly, while sda1 was not seen.
 
Doing fdisk -l shows that i have 1 partition type 83 linux on it + an extended partition (with the swap in there). Since i didn't install it, i have no idea why the swap is in an extended partition....
 
fsck /dev/sda1 gives me "Could this be a zero-length partition?". 
 
mk2efs -n shows the superblocks and partition info.
if i try to reset the backup of the superblock, it fails since the disk is in use ....??
 
if i look at it with gparted, the partition is marked unknown, with no data in it...
 
If i loose my partition ,so be it. There is no data on it. But it would be great if i could repair it, because otherwise i have to reinstall, customize, add applications, import settings, ..... 
 
Anyone an idea to try?

---

### Post by caljohnsmith on 2009-05-07
How about first posting:
```
sudo fdisk -lu
sudo vol_id --probe-all /dev/sda1
sudo mount /dev/sda1 /mnt
```
And we can work from there if you want.

John

---

### Post by Qtastic on 2009-05-07
root@ubuntu:/home/ubuntu# fdisk -lu

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a9fa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    76790699    38395318+  83  Linux
/dev/sda2        76790700    78236549      722925    5  Extended
/dev/sda5        76790763    78236549      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00066fda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241   83  Linux


vol_id --probe-all /dev/sda1 . no return


root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt
mount: you must specify the filesystem type
root@ubuntu:/home/ubuntu# mount -t ext3 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I booted with the live cd of Mepis and i had lots of io errors. i suspect a nearly dead disk....
I still have my second drive in this pc where i could shrink the home partition and have it setup as boot. i just wonder if i do this if all my settings will automatically ok.... should be, right?

---

### Post by Qtastic on 2009-05-07
Ok, I should have seen this :
dmesg contains all the errors of the disk :
[  648.895257] ata1.00: status: { DRDY DRQ ERR }
[  648.895260] ata1.00: error: { UNC }
[  648.895293] ata1: soft resetting link
[  649.071901] ata1.00: configured for PIO0
[  649.089014] ata1.01: configured for UDMA/100
[  649.089047] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  649.089052] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  649.089058] Descriptor sense data with sense descriptors (in hex):
[  649.089061]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  649.089071]         00 00 00 3f 
[  649.089075] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  649.089081] end_request: I/O error, dev sda, sector 63
[  649.089085] printk: 6 messages suppressed.
[  649.089089] Buffer I/O error on device sda1, logical block 0
[  649.089096] Buffer I/O error on device sda1, logical block 1
[  649.089099] Buffer I/O error on device sda1, logical block 2
[  649.089102] Buffer I/O error on device sda1, logical block 3
[  649.089105] Buffer I/O error on device sda1, logical block 4
[  649.089108] Buffer I/O error on device sda1, logical block 5
[  649.089111] Buffer I/O error on device sda1, logical block 6
[  649.089147] ata1: EH complete
[  649.141519] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  649.141531] ata1.00: cmd c4/00:01:3f:00:00/00:00:00:00:00/e0 tag 0 pio 512 in
[  649.141533]          res 59/40:01:3f:00:00/00:00:00:00:00/e0 Emask 0x3 (HSM violation)
[  649.141536] ata1.00: status: { DRDY DRQ ERR }
[  649.141539] ata1.00: error: { UNC }
[  649.141571] ata1: soft resetting link
[  649.319868] ata1.00: configured for PIO0
[  649.336999] ata1.01: configured for UDMA/100
[  649.337015] ata1: EH complete
[  649.391182] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  649.391196] ata1.00: cmd c4/00:01:3f:00:00/00:00:00:00:00/e0 tag 0 pio 512 in
[  649.391198]          res 59/40:01:3f:00:00/00:00:00:00:00/e0 Emask 0x3 (HSM violation)

and so on...

I suppose it4s dead?

---

### Post by Qtastic on 2009-05-07
sorry, posted the first question twice...

---

### Post by caljohnsmith on 2009-05-07
Yes, it does look like maybe the problem is with your HDD. How about running a SMART diagnostics test on your HDD so we can check its health:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so I can see the results.

John

---

### Post by Qtastic on 2009-05-09
Thanks for the help, but i think it is getting worse with the day.

The smartmontools don't seem to work. They give me an error that the disk doesn't support self testing.

I also now lost the other partition on that disk and the number of errors in dmesg is getting very large.

I just use the other disk (with the home partition on it) as boot and root partition and start all over again. It might even be good for the computer to have a fresh install instead of upgrades (started with 7.04 on it...).

Again, thank you very much for the help.

---

