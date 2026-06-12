---
title: "mdadm ntfs array 'missing signature'"
date: 2008-12-18
forum: General Help
---

### Post by touchlikefire on 2008-12-18
Good morning and hello,

PLEASE HELP: I've blown up my RAID array, or something, and I can't fix it.  

A while ago, I created the software raid0 array in Windows, and then wrote myself a script to call **mdadm** and mount it in ubuntu.  This script worked flawlessly:
```
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mount -t ntfs /dev/md0 /media/"Windows Backup"
```
My hdd's looked like:
[LIST]
[*]sda - 320 GB SATA boot
[*]sdb - 120 GB PATA slave (windows raid0)
[*]sdc - 80 GB PATA master (windows raid0)
[/LIST]

Then, I got a new hdd, created a bootable SATA array (hardware) such that my disks now look like:
[LIST]
[*]sda - 500GB SATA RAID0
[*]sdb - 320GB SATA RAID0
[*]sdc - 80GB PATA
[*]sdd - 120GB PATA
[/LIST]

Now, I can no longer access my softraid array on sdc/sdd from linux.  What's worse, is that i don't remember which drive was initially listed first in my script, the 80 or the 120 GB (since their letters have changed).

I have changed my script to reflect the new drive letters, but when I execute, I get the following:
```
mdadm: Cannot open /dev/sdc1: Device or resource busy
Failed to read bootsector (size=0)
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

I get the same as above if I swap the drive letters in my script (except the first line reads: "Cannot open /dev/sdd1...").

I really don't know the first thing about the content of my script, I wrote it off a tutorial I found on these forums, so I don't know how to begin troubleshooting, though I have tried.

I'm sure I could just boot into windows and read the array, but I no longer have windows on this machine (and putting it back on isn't an option right now).

Any help is direly needed, the softraid array has all my backup data, including my windows hdd images.

---

### Post by |{urse on 2008-12-18
try using chunk=128 instead.

You have changed the parity bit on sdb by switching the hard drives.

also sdb1 and sdc1 are the drives your script is using to build that raid

change it to suit which drives your raid is actually using

---

### Post by |{urse on 2008-12-18
try this instead

```
sudo mdadm --build /dev/md0 --chunk=128 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1
sudo mount -t ntfs /dev/md0 /media/"Windows Backup"
```

---

### Post by touchlikefire on 2008-12-18
Thanks for the quick response!

my script is a simple text file, the code of which is below:
```
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1
sudo mount -t ntfs /dev/md0 /media/"Windows Backup"
```

and
```
cfdisk /dev/md0:
FATAL ERROR: cannot open disk drive
press any key to exit
```

---

### Post by |{urse on 2008-12-18
yeah, I'm kind of stumped too.
Bump

---

### Post by touchlikefire on 2008-12-18
well!  I tried your modded script, and here is the output:
```
~$ sh raid
[sudo] password: 
mdadm: array /dev/md0 built and started.
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

This seems to be making progress.

---

### Post by |{urse on 2008-12-18
post the output of this

sudo dmraid -r

D'oh 

sudo apt-get install dmraid

first

---

### Post by touchlikefire on 2008-12-18
After the psuedo-success of my previous post, I have tried cfdisk again:
```
cfdisk /dev/md0
FATAL ERROR: bad primary partition 0: partition ends after end-of-disk
```

and inputting your command only shows the functioning SATA array:
```
sudo dmraid -r
/dev/sdb: nvidia, "nvidia_effcehjh", stripe, ok, 625142446 sectors, data@ 0
/dev/sda: nvidia, "nvidia_effcehjh", stripe, ok, 976773166 sectors, data@ 0

```

---

### Post by touchlikefire on 2008-12-18
NOTE: my RAID array is actually RAID0 striping on sdc/sdd, **not** RAID1.

---

### Post by jrusso2 on 2008-12-18
Did you break the mirror when you replaced the drive?  Then you rebuild the RAID

---

### Post by touchlikefire on 2008-12-18
I made a mistake when I wrote this post, it is actually a striped set, not a mirrored set.

---

### Post by |{urse on 2008-12-18
OH! well you will have to reassociate the drives the way they were to begin with. You probably lost your data? Anyone help this person?

---

### Post by touchlikefire on 2008-12-18
So, you're saying that my data is most likely irrecoverable?

---

### Post by |{urse on 2008-12-18
No i'm saying I don't know, but i would assume so if you are missing part of the stripe on a previously created raid1 that it would be irrecoverable.

---

### Post by touchlikefire on 2008-12-18
Blast!

Well...I shouldn't be missing anything?  All I did was add a new hdd, but I didn't physically move or otherwise rearrange anything.  When I installed the new hdd I put the SATA drives in striped RAID0 from the BIOS (which I now realize is more of a fakeraid, it's a nforce4 mobo), and installed Ubuntu on the SATA RAID.

This had the effect of changing my drives to the aforementioned, with my IDE drives relocated to sdc & sdd.  The pins and ribbon are physically connected the same as before, and I haven't done anything in software, either.

I had assumed I could just run my script after (re)installing Ubuntu and everything would be fine, and that's where I ran into this problem.

So to reiterate, I haven't changed anything with the IDE raid at all, I only added a new hdd.

Thoughts?

---

### Post by touchlikefire on 2008-12-18
Noting that changing ```
mdadm --build --chunk=64...
``` to ```
mdadm --build chunk=128...
``` yields the error that NTFS is possibly inconsistent and that seems like a real possibility to me, since we've all had ntfs drives show as needing an fsck when trying to mount them in linux after, say, windows had previously crashed.

In fact, that is exactly what had happened!  I remember now--I was in Windows (with my MS Windows created softRAID0 on the drives in question), when it BSODed on me and I said 'bump that' and just formatted the 320GB SATA drive since I was planning on going Linux-only anyway.

So, I conclude then that sdc & sdd are not inconsistent, and I am now wondering if there is anyway to override those flags so that I can mount /dev/md0?

```
# sh raid
mdadm: array /dev/md0 built and started.
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

# mdadm --misc --query /dev/md0
/dev/md0: 149.06GiB raid0 2 devices, 0 spares. Use mdadm --detail for more detail.

# # mdadm --detail /dev/md0
/dev/md0:
        Version : 
  Creation Time : Thu Dec 18 03:32:10 2008
     Raid Level : raid0
     Array Size : 156297216 (149.06 GiB 160.05 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu Dec 18 03:32:10 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1

```

---

### Post by |{urse on 2008-12-19
ill have a look at the mdadm man pages. I've never really messed with software raids on linux, only hardware.

---

### Post by touchlikefire on 2008-12-22
**SOLVED!** :-D

I was able to use one of the ntfsprogs tools, **ntfsfix**, to remove the dirty flag from the ntfs $logfile which was preventing **/dev/md0** from being mounted. Then I was able to run my script and the array mounted and is viewable again!

Here are the steps that led to success:
[LIST]
[*]Get mdadm to successfully load the array.  I did this by changing the "--chunk=" size from 64 to 128 in my [script]("http://ubuntuforums.org/showpost.php?p=6391521&postcount=1") per the instructions in comment [2]("http://ubuntuforums.org/showpost.php?p=6391544&postcount=2"), although I had to change it back later, FWIW. I also used **gparted** to identify which drives were the actual ones with the raid array so that I could input them into mdadm parameters (see my script if this is confusing).  When you successful load the array, you get this output: ```
mdadm: array /dev/md0 built and started.

```
[*]I then deduced that my ntfs striped partition was flagged as dirty and that was why I could not mount **/dev/md0** (see [here]("http://ubuntuforums.org/showpost.php?p=6391817&postcount=16") if you're curious)
[*]I used ntfsprogs (sudo apt-get install ntfsprogs) to enter:```
ntfsfix /dev/md0
``` which most importantly cleared the dirty flag from the NTFS $LogFile, allowing me to finally mount the drive. (see [manpage]("http://man.linux-ntfs.org/ntfsfix.8.html") for more info)
[/LIST]

---

