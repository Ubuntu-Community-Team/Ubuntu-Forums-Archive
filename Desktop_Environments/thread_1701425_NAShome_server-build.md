---
title: "NAS/home server-build"
date: 2011-03-06
forum: Desktop Environments
---

### Post by damorgue on 2011-03-06
[FONT=Arial][SIZE=2]I intend to build a NAS/homeserver. I have decided to use either Debian  or Ubuntu. I have also decided to build it now and not wait until btrfs,  although I might switch to it at a later point but that is irrelevant  for now. 64-bit versions of whatever i pick obviously. The objective is  to use mdadm raid5, possibly with LVM on top of that.[/SIZE][/FONT] [FONT=Arial][SIZE=2]

[B]Question 1:
Any major differences that I should care about between Debian and Ubuntu?

Question 2: [/B]*Went with Ubuntu 10.04 LTS*[B]
Any major differences between 10.04 LTS, 10.10 and the soon to be  relased 11.04 LTS? The differences, other than long term support, seem  really small, like kernelversions and small revisions.[/B]

Parts List:
AMD Athlon II X2 240e >>> 2,8GHz Dual Core with ECC-support
ASUS M4A78LT-M LE >>> GigE, 6xSATA, ECC-support
[/SIZE][/FONT] [FONT=Arial][SIZE=2]Kingston KVR1333D3E9S/2GEF[/SIZE][/FONT][FONT=Arial][SIZE=2] >>>[/SIZE][/FONT][FONT=Arial][SIZE=2] 2x2GB, ECC, DDR3[/SIZE][/FONT][FONT=Arial][SIZE=2]
PSU, case etc

I will most likely get a good NIC and a managed switch later on for bonding/LACP/link aggregation/teaming/trunking/802.3ad

Disks: (already have)
300GB or 8GB usbstick
2TB WD EARS

[B]Question 3:
Any suggestion on suitable drive that is not 4 times as expensive as the normal desktopdrives like the WD RE disks?[/B] *Went with the new 3-platter EARS*
Recently manufactured WD EARS can not enable TLER. [http://hardforum.com/showthread.php?t=1590200](http://hardforum.com/showthread.php?t=1590200)

Below is the plan of what I should do. I need help with the parts in **BOLD** and if you have any comments on the rest I would greatly appreciate it.

Set disks to ide-mode

[B]Q4: Change TLER/CCTL/ERC?
[/B]Depends on what drive I pick. NOT needed for software raid in with md
[B]Q5: Change headparking settings to disable such and avoid LCC-problem?
[/B]Depends on what drive I pick. wdidle3.exe in case of WD EARS. *Did that*

Once done, set disks back to ahci-mode

**Q6:  Install 64-bit Ubuntu Desktop on the 300GB and leave the default format  settings and let it create swap etc by itself on the 300GB disk.**
I intend to run the setup as follows...
/dev/sda 300GB
/dev/sdb 2TB
/dev/sdc 2TB
/dev/sdd 2TB
...where the 300GB is used for OS, programs, swap etc
and the latter 3 are used in a mdadm raid5 array "/dev/md0"

**Q7: Format using parted or fpart, mbr or gpt?**[/SIZE][/FONT][FONT=Arial][SIZE=2]
parted seems to be the best. *Partitioned correctly with parted*

[/SIZE][/FONT][FONT=Arial][SIZE=2]**Q8: All of this? [http://ubuntuforums.org/showpost.php?p=10366991&postcount=9](http://ubuntuforums.org/showpost.php?p=10366991&postcount=9)**[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]align at sector divisible by 8 in case of advanced format disk, some recommend 64, others 2048?[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]*Went with 2048 sectors*

After they have been formatted, I am planning to do this:
mdadm --create /dev/mdo --verbose --chunk=_ --level=6 --raid-devices=4 /dev/sd[xxxx]1[/SIZE][/FONT][FONT=Arial][SIZE=2]

[B]Q9: Create LV using LVM or a filesystem like xfs, ext2, ext3, ext4 etc?
[/B]mke2fs.
or mkfs.xfs
or another different filsystem
or something with LVM
(specify blocksize of 4k)Mount the /dev/md0 at /STORAGE[B]

Q10: What to do with '/etc/mdadm/mdadm.conf'?[/B]
The settings have to be saved there to load them at startup, right?

[/SIZE][/FONT][FONT=Arial][SIZE=2][B]Q11: Adding another 2TB disk to the array?
[/B]mdadm -add /dev/md0 /dev/sd_   #where _ is the new disk[/SIZE][/FONT][FONT=Arial][SIZE=2]
mdadm -grow /dev/md0 -raid-disks=_   #where _ is the new number of disks in the array[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2][B]Resize the filesystem across the new reshaped array?

Q12: Set up regular scrubbing of the array, cronjob perhaps?
[/B][/SIZE][/FONT][FONT=Arial][SIZE=2]Add this in cron.weekly:
echo check > /sys/block/md0/md/sync_action
[/SIZE][/FONT][FONT=Arial][SIZE=2]*I found out there is already such a scrub done monthly by default.*[B]

Q13: Share md0 using samba, cifs, nfs or something else?
[/B]*Went with samba, works fine*[/SIZE][/FONT]

[FONT=Arial][SIZE=2]** Q14: Set up link aggregation?**[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
[[FONT=Arial][SIZE=2]https://help.ubuntu.com/community/UbuntuBonding[/SIZE][/FONT]]("https://help.ubuntu.com/community/UbuntuBonding")[FONT=Arial][SIZE=2]
Or:[/SIZE][/FONT][FONT=Arial][SIZE=2]
[https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)[/SIZE][/FONT][FONT=Arial][SIZE=2]
Or:
[http://manpages.ubuntu.com/manpages/lucid/man4/lagg.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/lagg.4freebsd.html)

**Q15: What needs to have 'sudo' in front of it or administrator rights?** *I guess I'll notice as I go*[/SIZE][/FONT]

---

### Post by damorgue on 2011-04-07
Ok, I went ahead and have tried a lot since then, here is my current situation.

I went for raid6 isntead of raid5 to solve the problems with UREs during rebuild with these cheap-drives. Speaking of drives, i went with the WD20EARS-0MVWB0, The new 3-platter version of the 2TB. Below is a bench of one of them, they all perform the same.
[IMG]http://img4.imageshack.us/img4/9315/singledisk31ncq.png[/IMG]

I have 4 of these 2TB-disks that I have created a raid6-array out of. It might seem stupid to put only four disks in raid6 but I plan to add more. I actually already have more of them but I wish to create the array and then move the data from a couple of other 2TB disks to the array, after which I can add the now empty disks to the array.

This setup is expected to perform as such:
Read: 90%*average readspeed of one disk*number of disks
0,9*100*4 = 360 MB/s

Write: 90%*average writespeed of one disk*(number of disks-2)
0,9*100*2 = 180 MB/s

[B]*Is this expectation correct?*
*Is 90% a reasonable efficiencyfigure that counts the losses in a raidarray?*[/B]

I have tried creating the array with several different:
Chunksizes (aka stripesizes) from 64KB to 512KB
Readahead set to 65536 instead of standard value
stripe_cache_size set to everything from 256 to 32768
max ncq queue set to values between 1 and 31

I have a lot of graphs from my testing but I can summarize it like this:
Setting max quene to 1 on the disks in the array increases performance by a couple of percent. Readahead increased performance slightly. Stripe cache increase performance slightly further and chunksize at 256 or 512 seems to be the best performing. The differences between all these settings is however negligible. I am far from the performance some other people are getting from similar arrays as seen below.
[IMG]http://img855.imageshack.us/img855/9330/512chunk1ncq32768cache.png[/IMG]

I am quite sure that I have formatted the disks correct since
A) the partitions begin at sector 2048 and since
B) a raid0-array is created with the same disks they perform as they should. They reach average reads and writes of about 350MB/s.
[IMG]http://img146.imageshack.us/img146/2012/raid0256chunk31ncqtry2.png[/IMG]
This is close to 0,9*100*4 which is the expected performance. One can thus draw the conclusion that the partitions are aligned.

[I][B]What have I missed?
Is there anything else I can do to increase performance?

[/B][/I]_If a mod reads this, feel free to move it to another category like server since I have done everything but the performancetests in the terminal. Might be more appropriate._

---

### Post by damorgue on 2011-04-07
Are my expectations way off?
If the expected read-performance is:
0,9*(n-2)*(readspeed for one disk)
then the array performs quite excellent.

Edit: It would seem as both read and write performs 0,9*(n-2)*(speed) with raid6, stupid me.

---

