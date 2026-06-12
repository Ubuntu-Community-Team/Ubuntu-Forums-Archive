---
title: "Ext4 died"
date: 2009-06-16
forum: General Help
---

### Post by bodhi.zazen on 2009-06-16
It appears I just lost an Ubuntu install.

Ext4 file system, unexpected power failure.

Boot drops to busy box ...

From a live CD :

> root@ubuntu:~# fsck -y /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway? yes

fsck.ext4: unable to set superblock flags on /dev/sda1
> root@ubuntu:~# fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? yes

fsck.ext4: unable to set superblock flags on /dev/sda1> root@ubuntu:~# fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? no

Clear journal<y>? no

/dev/sda1: clean, 138871/373152 files, 681246/1492029 blocks

root@ubuntu:~# fsck -y /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway? yes

fsck.ext4: unable to set superblock flags on /dev/sda1> root@ubuntu:~# fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? no

Clear journal<y>? yes

/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 138871/373152 files (0.2% non-contiguous), 681246/1492029 blocks> root@ubuntu:~# mount -t ext4 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# dmesg | tail
[ 1894.643462] JBD: recovery failed
[ 1894.643468] EXT4-fs: error loading journal.
[ 1894.645367] sd 0:0:0:0: [sda] 12582912 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[ 1894.645385] sd 0:0:0:0: [sda] Write Protect is off
[ 1894.645387] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1894.645404] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1894.645422] sd 0:0:0:0: [sda] 12582912 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[ 1894.645432] sd 0:0:0:0: [sda] Write Protect is off
[ 1894.645434] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1894.645450] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA> root@ubuntu:~# mke2fs -n /dev/sda1
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
373152 inodes, 1492029 blocks
74601 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1530920960
46 block groups
32768 blocks per group, 32768 fragments per group
8112 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736

root@ubuntu:~# e2fsck -b 32768 /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda1: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
e2fsck: unable to set superblock flags on /dev/sda1

YIKES :( 

Suggestions anyone ?

:lolflag:

---

### Post by nolliecrooked on 2009-06-16
> **bodhi.zazen said:**
> It appears I just lost an Ubuntu install.

Ext4 file system, unexpected power failure.

Boot drops to busy box ...

From a live CD :



YIKES :( 

Suggestions anyone ?

:lolflag:

re-install :P

---

### Post by 4Orbs on 2009-06-16
When it happened to me it wasn't even a power failure, just a system lockup during some vigorous copy/paste activity. I couldn't fix it. And when I deleted the ext4 partitions, the reformatting of the new unallocated space to ext3 took an unusually long time.

---

### Post by brncao on 2009-06-16
A user warned me not to use ext4 yet because of that. So I stuck with ext3. Reformat?

---

### Post by ActiveFrost on 2009-06-16
Lesson #1 - use UPS :) More on-topic - reinstall !

---

### Post by nolliecrooked on 2009-06-16
out of curiosity, did you make a seperate /home folder, and use swap?

---

### Post by bodhi.zazen on 2009-06-16
I use a /data partition and not a /home partition so yes I keep my personal data separate from my OS.

Yes I have a swap partition.

I know I can re-install from back up, I am wondering if anyone has a fix.

If no solution is offered in the next day or so I shall re-install.

I am also going to revert to ext3 for the time being, at least for backups.

---

### Post by ibuclaw on 2009-06-16
To quote Tso himself, you could try:


```
e2fsck -b 32768 -B 4096 /dev/sda1
```
As...
> 
That forces the use of the backup superblock right away, and might help you get past the initial error.

Iain

---

### Post by hal8000 on 2009-06-16
I've never lost data on any linux filesystem, so your post is scary. I've once had a powercut during a thunderstorm but was on a resiser filesystem and recovery was possible from an alternate superblock.

I found this superblock recovery (for Sun)
[http://marc.info/?l=linux-ext4&m=123140952031871&w=2](http://marc.info/?l=linux-ext4&m=123140952031871&w=2)

you'll need to compile it for linux, but it may help to find an alternate superblock on ext4 file systems.

Luckily your /home is ona separate partition but perhaps testdisk may recover something from your / partition if any other files need restoring.
Hal

---

### Post by lovinglinux on 2009-06-16
> **hal8000 said:**
> I've never lost data on any linux filesystem, so your post is scary. I've once had a powercut during a thunderstorm but was on a resiser filesystem and recovery was possible from an alternate superblock.

Yes it is scary. I guess I'm lucky, because I had several power failures since I started to use ext4 and none of them resulted in any errors.

---

### Post by sdennie on 2009-06-16
I hate to say it but...  I told you so!  ;)

---

### Post by binary10 on 2009-06-16
Some die - some don't. Keep an open mind... 

I did an experiment on my laptops encrypted lvm'd ext4's USB system drive.. ok it was my old test system copy. I pulled the usb plug on it while logged in. wasn't really doing much.. conky was running monitoring cpu etc..  I tried a few directory lookups... I plugged it back in again.... took it out again and started to do a bit more writes etc.. thats when it went a bit odd. But I booted it back up.. 

I've stuck with ext4, my rsync backups handle will handle any major issues.

To quote some of the foo's - Its times like these you learn to live again.

---

### Post by VMC on 2009-06-16
> **bodhi.zazen said:**
> I use a /data partition and not a /home partition so yes I keep my personal data separate from my OS.

Yes I have a swap partition.

I know I can re-install from back up, I am wondering if anyone has a fix.

If no solution is offered in the next day or so I shall re-install.

I am also going to revert to ext3 for the time being, at least for backups.

Are you doing those fsck from another livecd, like Parted Magic? 

Also, I've had at one power failure, and at least 3 times that I just powerded off my computer without regards to Ext4 or anything. On next boot, Linux kernel complained about it then auto-ran fsck. One of those power cycles was because of SATA data cable corruption. But I have **NEVER** had it not boot up. I have to add, that I have a swap partition and one Ubuntu "/" partition. that's all.

---

### Post by blueridgedog on 2009-06-16
The final command you posted shows you tried to reformat the offending partition.  Have you thought of deleting it and remaking it?  Perhaps I have miss read the last command.

---

### Post by bodhi.zazen on 2009-06-17
> **blueridgedog said:**
> The final command you posted shows you tried to reformat the offending partition.  Have you thought of deleting it and remaking it?  Perhaps I have miss read the last command.

That is what I would have thought, I needed to consult the man pages.

mke2fs -n /dev/sda1

 -n     causes  mke2fs  to not actually create a filesystem, but display
               what it would do if it were to create a filesystem.  This can be
               used  to  determine the location of the backup superblocks for a
               particular filesystem ...

---

### Post by Steelmourne on 2009-06-17
Using ext4 after system reinstall. No problems yet. Seems snappier than ext3 too.

---

### Post by bodhi.zazen on 2009-06-17
OK, just an update ....

I ran tinivole's command : Same results as "e2fsck -b 32768 /dev/sda1" (without the "B" flag).

Still no joy :(

As I was running the live CD anyways, I went for "Data recovery" -> Tried to install testdisk (photorec) -> apt-get hung -> machine (and keyboard) unresponsive -> had to hard reboot :rolleyes:

I decided just for grins to boot the hard drive -> 

lo an behold, despite errors on the live CD it boots :twisted:

The system seems to be running normally again, not entirely sure what fixed it.

Thanks to the people who offered assistance. Hope this thread helps somebody else recover.

---

### Post by fillintheblanks on 2009-06-17
once you go EXT4, you never go back :twisted:

---

### Post by VMC on 2009-06-17
> **bodhi.zazen said:**
> ...
I decided just for grins to boot the hard drive -> 

lo an behold, despite errors on the live CD it boots :twisted:

The system seems to be running normally again, _not entirely sure what fixed it._

Thanks to the people who offered assistance. Hope this thread helps somebody else recover.

That is the troubling part. To fix something and not know what it was that fixed it. Apparently though, one of the commands entered did the trick.

---

### Post by bodhi.zazen on 2009-06-17
> **sdennie said:**
> I hate to say it but...  I told you so!  ;)

Pffttt

:lolflag:

---

### Post by T-Train on 2009-07-25
I had the same problem, they system became read only and froze.  At first I thought it was the hardware or a temp issue.  I bought a new drive and the same issue occurred.  I am not sticking to ext3.

---

### Post by munky99999 on 2009-07-25
> Ext4 file system, unexpected power failure.
Ouch.

From a live CD :

> mount: wrong fs type, bad option, bad superblock on /dev/sda1,

older hard drive? Or overtaxed IOs?

```

sudo badblocks -snv /dev/sdb

```

It will non-destructively check the hard drive for bad blocks. It will take awhile.

You could also try 

```
badblocks -swv /dev/sdb6

```

That one will destructively check the hard drive. It will be rather quick.

I think the power failure is more of a catalyst for larger problem.


Alternatively you might wanna grab a persistent live usb. or fedora 11. That way you will get the Smart hard drive tools.



Personally Ive had the problem with ext3 and such also. Ultimately was because the hard drives being old and bad.

---

### Post by Virtual DarKness on 2009-07-25
> **bodhi.zazen said:**
> It appears I just lost an Ubuntu install.

Ext4 file system, unexpected power failure.

Boot drops to busy box ...


try to boot with the old kernel if you still have it in grub, it worked for me.

bye,
Giovanni.

---

