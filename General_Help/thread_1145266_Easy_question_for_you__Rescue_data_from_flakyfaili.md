---
title: "Easy question for you??  Rescue data from flaky/failing HDD"
date: 2009-05-01
forum: General Help
---

### Post by NooB Frank on 2009-05-01
I have setup a dual boot system with linuxmce and mythdora booting off of my first 30 gb ide hd.  I stored my recordings and songs etc on a second 320gb Hitachi ide hd plus had my swap partition there.  Things were going along so so.  Let&#8217;s just say - I'd run into something and research and learn something new.  Well - now I am in sortof a jam.  In fact I am not sure where to start.  With each piece of evidence I google I find 5 more branches and I am just overwhelmed.

I think this started when i was adding a 3rd boot option.  Used gparted to add another partition and added a third linux operating system.  Anyway - started having intermittent difficulties finding my recordings and now I can't even see the drive. 

For trouble shooting &#8211; I have pulled IDE1 and moved the flaky drive to primary.  

Using Hitachi drive fitness test software from boot cd (I have a Hitachi drive &#8211; mfg in July 2008 ) it checks the drives and errors out with the 0x70 - corrupted sector error.  Of course for some reason if I click to repair it - the software tells me it is not a Hitachi drive and refuses to repair it.  

Ok - so using Mepis live cd - I looked at the drive in Gparted.  Turns out the boot flag was on in the first partition - where I installed my latest linux try.  I don't know if pc's like having two drives both with a boot flag on??  I used Gparted to turn the flag off.  

No matter what though &#8211; it would not let me mount any partition of the drive.  Currently if I try to mount the recordings partition in Gparted &#8211; it says Could Not Mount:  wrong fs type, bad option, bad superblock on /dev/sda6, missing codepage or other error.

Sometimes in Gparted there is a warning flag that says:  dumpe2fs: No such file or directory while trying to open /dev/sda6.

Sometimes when I try to boot the Mepis live CD it locks up on:  
waiting for /dev to be fully populated.  &#8211; and never loads the os.

Okay - so I think the drive is getting flaky and failing.  So my questions are:
1.  How can I make sure it is dead/dieing?
2.  If I can get it recognized long enough - what is the best way to force it to mount and copy the data over to an external usb drive?
3.  If it is not bad and is flaky because of my goofing around with it - what do I need to do to get it back acting normal?

Thanks in advance and any help even if pointing in a research direction is appreciated.

Frank

---

### Post by jbrown96 on 2009-05-01
The hitachi software probably reads the SMART data from the drive, but you may want to install a utility to check that data. I believe that there is one called gsmart or something. Just search in Synaptic.


I would recommend copying the data at the block level, and then try to copy it. I would under no cirumstances mount that parition. Furthermore, if you have 1GB of ram, disable swap. You can run ```
sudo swapoff
```, but you need to disable it on boot as well. Remove it from /etc/fstab. 

To copy at the block level, you will need another drive that is at least 320GB. Find your device names using fdisk -l. You are looking for /dev/sdb1 or whatever for your device and also the backup drive. 
THIS IS EXTRAORDINARILY IMPORTANT THAT YOU IDENTIFY THE DEVICES CORRECTLY!!!! If you make a mistake here, everything will be lost.
You want to use the whole device. So if your recordings are on /dev/sdb1, use /dev/sdb. 
```
,sudo dd if=/dev/SOURCE of=/dev/DESTINATION
``` replace source with sdb or whatever you found in the last step and similarily for DESTINATION. The command will not run until the comma is removed at the beginning. Take a minute, look over the command, step away from the computer, and make sure that it is typed correctly. Remove the comma and execute. It won't give you any output and will take a while so be patient. 


Copying at the block level is the best because there is no unneccessary disk activity going on. This should give you the best chance to get the data off. The only downside is the size of backup drive required. 


Even if you end up copying the files normally, make sure to turn your swap off. In the future, it would be a good idea to keep your swap off of your data device because it reduces the life of the drive since it has to spin up more often.

---

### Post by NooB Frank on 2009-05-01
Thanks very much!!
I like the sounds of this!!
But here are a handful of stupid questions.

I am booting currently from a live CD.  I don't understand how to disable swap on startup?  I understand the sudo swapoff command.  But explain “remove from /etc/fstab”.  Would it be easier if I put the troubled drive in an external drive/usb setup?  Will that eliminate any swap issues?  I do have 1GB ram.

Can the drive I copy TO have more than one partition?  I only have one drive bigger than 320gb and it isn’t empty either.  It is in an another external hard drive case too.  

I am okay with looking for and identifying each drive as /dev/sdb1 etc.  And certainly I understand your caution!!  

Once I copy the data to the other drive – are there any steps I need to take to make the files usable or ??

Thanks again for all your help!!

Frank

---

### Post by logos34 on 2009-05-01
if dd chokes on read errors, there's [ddrescue]("http://www.garloff.de/kurt/linux/ddrescue/")

either run the swapoff command in terminal or System>admin>partition editor>right-click swap>swapoff

---

### Post by jbrown96 on 2009-05-01
If you boot from a liveCD, then it will automatically use any swap partitions it finds. Swapoff will be necessary each time you boot from it. The /etc/fstab is a file that lists all partitions that should be mounted automatically. You could remove your swap entry from there, but it would only matter if you are booting the installed system, so don't worry about it.


You can place it on a partition. You will need to change the dd command though. You don't want to use the raw devices (/dev/sdb); use the partitions instead (/dev/sdb1). Don't copy over your swap partition, which would probably be /dev/sdb2. There may be problems mounting it this way. You will need to create a partition identical to the one that you are having problems with; make sure that it is the same type and has the same number of blocks (can check with sudo fdisk -l). 

The important thing is to get the data off disk as soon as possible. It may turn out that you can't mount the data that you copied with dd, but once you replace the drive, you shouldn't have any trouble copying it to the new one and mounting it. 

I forgot about ddrescue. You should use that tool instead. ```
sudo apt-get install ddrescue
``` I haven't used it (knock on wood), but I can try to help if you need it. A manual is available once you install ```
man ddrescue
```


Edit:
Here's an idea that might work really well, but I haven't tried it. Use ddrescue to copy from your corrupted partition (a block device) and save it to a file on your external USB device. 

Someone else should check this, but looking at the man page I think you could use. ```
sudo ddrescue /dev/sdb1 /media/disk/backup
``` replace sdb1 and /media/disk/backup with the proper places. This is going to be a huge file. I'm guessing that your recordings occupy most of the space, so it will be ~320GB. Wikipedia shows that you should be fine with a file this large as long as you are using a Linux FS (ext3, ext4, reiserFS, JFS, and XFS).

You may be able to mount this file. You would mount it the same as anything else, maybe with a loop-back option(?).
```
sudo mount -t auto /media/disk/backup /media/test -o loop
``` you will need to create /media/test or where ever you want to mount it.

---

### Post by NooB Frank on 2009-05-01
Okay - working on that now. 

Thanks for your help.

---

### Post by NooB Frank on 2009-05-01
Ok - new info...

I think that my data table is screwed up somehow.  I did the fdisk -l command and got to looking at the table...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         851     6835626   83  Linux
/dev/sdb2             852       38913   305733015    5  Extended
/dev/sdb5             852        1181     2650693+  82  Linux swap / Solaris
/dev/sdb6            1182       38913   303082258+  83  Linux


It looks like the partitions overlap.  Or sdb2 includes sdb5 and sdb6?  Is that normal?

If I got your advice right I think my command is going to be
sudo ddrescue /dev/sdb6 /dev/sdc1/lostrecordings 

And then somehow I will be able to mount that huge file as a partition or something.  Either way - getting the data somewhere fast sounds key.

Thanks again guys.

Frank

---

### Post by jbrown96 on 2009-05-01
/dev/sdb2 is a extended partition, meaning that it is a container for other partitions.

That's not the command that you want. You want to take a block device as the source (/dev/sdb6) and output to a file. You can't access files on a block device with /dev/sdc1/lostrecordings. You need to mount /dev/sdc1 somewhere, then save the data from your block device to the mount point. 
ubuntu mounts disks automatically to /media/disk, /media/disk-1, /media/disk-2, etc. Just insert your disk, then double click the icon on the desktop and use the "up" button to firgure out where in /media you are. 

```
sudo ddrescue /dev/sdb6 /media/disk/lostrecordings
``` replace disk with disk-1 or whatever, depending on where it's mounted.

---

### Post by NooB Frank on 2009-05-01
Cool!!!
Thank you thank you thank you!

I think I got it figured out and it is copying now.  I will report back later (much later if ~320GB to copy).  

Thanks again!

Frank

---

### Post by NooB Frank on 2009-05-01
Well things are moving along. 

It seems to be 1/3 done and about 3% is bad data.  I don't know what that will look like in the end but we will keep moving.

But considering this probably won't be done for several more hours I thought I'd ask about the next step

> You may be able to mount this file. You would mount it the same as anything else, maybe with a loop-back option(?).
Code:

sudo mount -t auto /media/disk/backup /media/test -o loop

you will need to create /media/test or where ever you want to mount it.

I am guessing this will mount that huge file as a location within linux.  Once I direct file manager there it will show the various files just like they were on the drive?  Then I can drag and drop them to another location?  

Oh and to make it more exciting - I'd like to drop them on the same external hard drive that I am storing this huge backup file on.  

Not sure what the loop back does but - let me know if I have this understood correctly. 

Thanks again!

---

### Post by jbrown96 on 2009-05-01
I'm not really sure about the loop-back part. I know that if you have a CD image (.iso) you have to mount it with the loop option. You can try it either way. The system will only complain if it's wrong. You shouldn't have any problems copying to the same drive, provided you have enough free space. 

I've never recovered data from a bad partition, so I don't know how that 3% will affect your recovery. you might lose some files, but I imagine that it will be possible to recover the majority.

---

### Post by NooB Frank on 2009-05-02
Still going...

In fact - it is at 600mb copied.  It's been about 12 hours give or take.  So unless it starts flying somehow - it looks like it will take 260 days to complete this?  

If that is the case - is there another way?  Can I stop and go to step 2 with the file and see if the data is even in tact enough?

Just anxious.

Thanks

---

### Post by codeseer on 2009-05-02
> **NooB Frank said:**
> Still going...

In fact - it is at 600mb copied.  It's been about 12 hours give or take.  So unless it starts flying somehow - it looks like it will take 260 days to complete this?  

If that is the case - is there another way?  Can I stop and go to step 2 with the file and see if the data is even in tact enough?

Just anxious.

Thanks

That's pretty slow, unless it's making several passes to try to get the best copy or merge copies, which I'm not aware that dd does. There are products that do that. I would say the drive is definitely damaged if it's taking that long. It may take a long time to do. You may want to consider taking it to a data recovery place that has hardware designed for that, if your data is very valuable. If you don't have a lot of data you want to really recover, you might consider file carving.

---

### Post by NooB Frank on 2009-05-02
It is not worth enough for commercial recovery.  But always looking to learn any DIY tricks I can.

File Carving??  Do tell.

---

### Post by codeseer on 2009-05-02
> **NooB Frank said:**
> It is not worth enough for commercial recovery.  But always looking to learn any DIY tricks I can.

File Carving??  Do tell.

[http://www.forensicswiki.org/wiki/Carving](http://www.forensicswiki.org/wiki/Carving)

I've done it with a hex editor before as well... Sometimes the hex editors designed for this are called 'drive editors'.

---

### Post by jbrown96 on 2009-05-02
You can stop it; the only thing is that you've put 12 hours of wear on a damaged drive, but it's just not transfering at an acceptable rate. 

Try stopping ddrescue and mounting the incomplete file. ```
sudo mount -t TYPE /media/disk/lostrecordings /MOUNT/FOLDER -o r force loop
``` Change TYPE and mount folder. You may have to remove loop. 

You can also try to mount the drive directly, using the same command but change /media/disk/lostrecordings to /dev/sda6. Make sure you do it read-only and specify the type. 

If that still doesn't work, try using dd instead of ddrescue. It shouldn't take that much time since it does error checking.


Did ddrescue give you any output that could be helpful? You can try ddrescue again with options to give you more output and not retry on errors. This may help determine where the errors are. ```
sudo ddrescue -nvv /dev/sdb6 /media/disk/lostrecordings
``` I'm not sure how much verbosity it supports, so you may need to remove one of the v's.

---

### Post by NooB Frank on 2009-05-02
Well - here is where it got to.  

```
mepis1:~# ddrescue /dev/sdb6 /mnt/sdc1/lostrecordings


Press Ctrl-C to interrupt
rescued:   940302 kB,  errsize:  35594 kB,  current rate:     1927 B/s
   ipos:   975896 kB,   errors:     861,    average rate:    13209 B/s
   opos:   975896 kB
Interrupted by user

```

The copy rate would go way up and way down.  

Okay - trying to do the mount trick just to see what 19 hours of copying got. ..

```


# sudo mount -t ext3 /mnt/sdc1/lostrecordings /mnt/sdc1/dlostrecordings -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


Typing with the force loop gives a general mount command misuse error.

```
dmesg | tail
EXT3-fs error (device loop1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 3120627712)!
EXT3-fs: group descriptors corrupted!
EXT3-fs error (device loop1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 3120627712)!
EXT3-fs: group descriptors corrupted!
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
EXT3-fs error (device loop1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 3120627712)!
EXT3-fs: group descriptors corrupted!
EXT3-fs error (device loop1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 3120627712)!
EXT3-fs: group descriptors corrupted!

``` 

Here is the tail thingy.

Anyway - I'd love to see what it copied if you can help me with the syntax of the mount command.  I am showing my ignorance here on linux file systems I bet but learning.

Thanks again,

---

### Post by jbrown96 on 2009-05-02
It doesn't look like this is going anywhere. Let's try using fsck instead. 

first, find your backup superblocks
```
sudo mke2fs /dev/sda6
``` This should print out a list of backup superblocks.

Try to fsck the partition with the normal superblock.
```
sudo e2fsck -C 0 -y /dev/sda6
``` If you get an error about a bad superblock, then try the command again ```
sudo e2fsck -C 0 -y -b X /dev/sda6
``` where X is a backup superblock found from mke2fs.

[Source]("http://admon.org/node/96")
you should also read the manpage first. ```
man e2fsck
``` and ```
man mke2fs
```

Edit: It looks like your files might be moved to a folder called Lost+Found if it works.

---

### Post by NooB Frank on 2009-05-04
Well - I ran

sudo e2fsck -C 0 -y /dev/sdb6

I let it cook 18 hours or so...  and it just ran into error after error...

```
Error reading block 20742533 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error? yes

Force rewrite? yes

Error reading block 20742535 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error? yes

Force rewrite? yes

Error reading block 20742546 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error?     yes

Force rewrite? yes

Error reading block 20742548 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error? yes

Force rewrite? yes

Error reading block 20742549 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error? yes

Force rewrite? yes

```

So I canceled it. Best I can figure - it got through 20 MB in 18 hours?

Right now I am trying one more thing before I just give up.

I am adding 330 GB partition to my 1T external drive.  Then I will try ddrescue partition to partition copy with the log on and see what it looks like.  

I plan to run something like this:
```
mepis1:~# ddrescue -n /dev/sdb6 /dev/sdc2.log

```

But essentially - I am thinking that the data is pretty well toast and I need to move on. 

Of course I am open to other thoughts.  

Tons of thanks to JBrown96 for the help.  Thanks also to codeseer.  I learned a ton and couldn't have done any of this without the help.

I will keep this thread open and post what happens even if it doesn't work - in case it helps the next guy.

Frank

---

### Post by NooB Frank on 2009-05-08
Well - got busy so I didn't get as much done. 

But - here is what I did do...

I tried Spinrite.  It isn't free - but I figured if it worked it would be a handy tool to have.  

Well - it sorta looked like it would work... if I had 370 days to run it.  No kidding - it wanted 8900 hours more scan time. 

But a couple of interesting notes - it said it was having trouble because the drive was reported incorrectly in the BIOS...  Now this is an old machine maybe they don't have ability to support 320GB drive?  Or - is it pointing back to some little thing wrong with the drive.  It is less than 1 year old and catastrophic failure just didn't seem likely...

I read somewhere to put a bad drive in the freezer.  So it has been chilling for a few days. 

Okay - so today I booted my live disk of ubuntu and opened file manager and boom - it showed up...  It failed to mount - but lately it wasn't even showing up.  

So I did a dmesg | tail and...

```
ubuntu@ubuntu:~$ dmesg | tail
[ 1132.583204] sd 0:0:0:0: [sda] 80418240 512-byte hardware sectors: (41.1 GB/38.3 GiB)
[ 1132.583302] sd 0:0:0:0: [sda] Write Protect is off
[ 1132.583305] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1132.583551] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1132.583596] sd 0:0:1:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[ 1132.583619] sd 0:0:1:0: [sdb] Write Protect is off
[ 1132.583622] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 1132.583658] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1138.540420] EXT3-fs: no journal found.
[ 1147.437280] EXT3-fs: no journal found.

```

It says EXT3-fs : no journal found.  

I am wondering if this is just a little tweak??

Is there a way to rebuild a EXT3 journal?

Thanks again,

---

### Post by nogasbiker on 2011-03-03
> **jbrown96 said:**
> It doesn't look like this is going anywhere. Let's try using fsck instead. 

first, find your backup superblocks
```
sudo mke2fs /dev/sda6
``` This should print out a list of backup superblocks.


Doesn't this write a new filesystem over /dev/sda6?  It will write out a list of superblocks, but *new ones*.  It won't find existing superblocks?

Sorry to dredge up an old thread   :)    But this one gave me pause

---

### Post by NooB Frank on 2011-03-03
WOW... this has been a while.  Okay - I have the old drive here somewhere but honestly i have moved on.  

Whatcha mean that this thread gave you pause?  I am not sure I remember everything I tried.  

Is there something you think I should try or were you just thinking that I was instructed to write over my superblocks.  If so - realize I had all but given up. 

Anyway - I will keep this open if you have an answer for me to try to pass on the knowledge to the people.  Otherwise - I have learned to live without the data. 

Thanks either way 
Frank

PS - Still a Linux lover trying to plant little seeds here and there.  Of course I type that on a dual boot Win7/Ubuntu pc wishing I could cut the cord 100% from Winblows one day...

---

