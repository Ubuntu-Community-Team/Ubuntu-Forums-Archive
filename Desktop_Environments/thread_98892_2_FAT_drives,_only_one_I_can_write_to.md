---
title: "2 FAT drives, only one I can write to"
date: 2005-12-04
forum: Desktop Environments
---

### Post by DFreeze on 2005-12-04
I've put this in another thread as well, but that was when I thought it was an fstab-thing. Now I'm not so sure...

I have two FAT disks, mounted exactly the same, both show drwxrwxrwx (or something) in the properties, but I can't write anything to one of them. The other one is fine.

Even with sudo nautilus I can't do a single thing... 

Any suggestions where to look, other than fstab-settings?

---

### Post by doitashimashite on 2005-12-04
Are you sure they are mounted in exactly the same way?
Are you sure both are (v)fat? Isn't by coincidence the problematic one a NTFS filesystem?

---

### Post by aysiu on 2005-12-04
Just so we can verify that what you're saying is true, can you post the output of these commands? ```
df -h
sudo fdisk -l
cat /etc/fstab
```

---

### Post by doitashimashite on 2005-12-04
[QUOTE=aysiu]Just so we can verify that what you're saying is true, can you post the output of these commands? ```
df -h
sudo fdisk -l
cat /etc/fstab
```[/QUOTE]

I would suggest doing fdisk -l on *both* drives:

sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdb

(replace hda and/or hdb by the drives you use)

---

### Post by aysiu on 2005-12-04
[QUOTE=doitashimashite]I would suggest doing fdisk -l on *both* drives:

sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdb

(replace hda and/or hdb by the drives you use)[/QUOTE] You may know more about this than I do, but doesn't ```
sudo fdisk -l
``` list partition information for all partitions on all drives?

---

### Post by doitashimashite on 2005-12-04
[QUOTE=aysiu]You may know more about this than I do, but doesn't ```
sudo fdisk -l
``` list partition information for all partitions on all drives?[/QUOTE]

Assuming that these partitions are all listed in /proc/partitions (and I don't see any reason why they shouldn't) then yes, you are right.

---

### Post by DFreeze on 2005-12-05
Ok, I'll try to put all the requested info in here:

**~$ df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             8,3G  3,8G  4,2G  48% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-k7/volatile
/dev/hda1             9,6G  2,5G  7,1G  26% /media/hda1
/dev/hdb1              77G   68G  9,0G  89% /media/hdb1
/dev/hdc1              19G  712M   19G   4% /media/hdc1

**~$ sudo fdisk -l**
Schijf /dev/hda: 20.4 GB, 20416757760 bytes
255 koppen, 63 sectoren/spoor, 2482 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        1241     9968301    7  HPFS/NTFS
/dev/hda2            1242        2335     8787555   83  Linux
/dev/hda3            2336        2482     1180777+  82  Linux swap / Solaris

Schijf /dev/hdb: 81.9 GB, 81964302336 bytes
16 koppen, 63 sectoren/spoor, 158816 cylinders
Eenheden = cylinders van 1008 * 512 = 516096 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1               1      158802    80035798+   c  W95 FAT32 (LBA)

Schijf /dev/hdc: 20.4 GB, 20404101120 bytes
240 koppen, 63 sectoren/spoor, 2635 cylinders
Eenheden = cylinders van 15120 * 512 = 7741440 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdc1   *           1        2635    19920568+   c  W95 FAT32 (LBA)

**~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1    vfat    umask=000                0       0
/dev/hdc1       /media/hdc1     vfat    umask=000        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I hope you can see something I'm missing here... BTW I've tried all sorts of gid=1000, rw, user, auto, whatever settings behind the vfat, so I'm pretty sure that's not the way to go here.

Thanks for all your help so far. I hope we can fix this together!

---

### Post by metoo on 2005-12-06
So what are the two partitions you want to write to?

hdb1 and hdc1 should be OK. hda1 is ntfs, you cannot write to it by default.

---

### Post by DFreeze on 2005-12-06
Sorry, forgot to clarify. 

hdb1 is the one causing trouble, hdc1 is doing fine...

---

### Post by doitashimashite on 2005-12-06
[QUOTE=metoo]So what are the two partitions you want to write to?

hdb1 and hdc1 should be OK. hda1 is ntfs, you cannot write to it by default.[/QUOTE]

That's right, and I'd like to add not only *by default*, but no matter how hard you try, it won't work. I spent hours trying to mount an nfts partition rw and I finally gave up.

---

### Post by doitashimashite on 2005-12-06
@ DFreeze: try this:

sudo gedit /etc/fstab

Change the line referring to /dev/hdb1 into:

/dev/hdb1 /media/hdb1 vfat noauto,user,uid=<your user id>,gid=users

Finally, (re)mount /dev/hdb1.

Does this help?

---

### Post by DFreeze on 2005-12-10
I'm sorry to say it doesn't. I've done exactly what you described above. After that I tried some combinations again, put umask=0000 back in in combination with your suggestion, put rw,noauto,... in it, but still nothing.

I noted something strange: if I right-click, I see "Make Folder" **not** greyed out, so nautilus knows somewhere that I'm allowed to do that. But when I click it, it says "Error: Read Only Filesystem" (translated from Dutch). 

Does anyone here have any suggestions left?

---

### Post by DFreeze on 2005-12-11
Well, it's not a GNOME thing either. I can't write to the disk in KDE as well. Could it be I've installed a faulty Breezy-disk (I didn't do a checksum with the ISO), and somewhere deep inside some settings-file there's an option wrong?

---

### Post by aysiu on 2005-12-11
It can't be a Breezy thing. If it works with one drive and not the other, it sounds as if the one drive it's *not* working on is faulty in some way... or not really FAT.

---

### Post by soulestream on 2005-12-11
do you get an error when you use

mount -a

or 

mount /mnt/hdb1


have you tried creating a file or directory from command line


soule

---

### Post by DFreeze on 2005-12-12
Mounting gives no error. In another thread (which I will redirect to this thread since they after all cover the same issue) someone said that the disk may be faulty. I can read from the disk with no problem, would that still make sense?

I must add that it is indeed a buggy drive (but it's the biggest I have so I'd regret having to trash it). Sometimes it makes clicky sounds (sounds like parking the diskheads) and stalls the system. But this is not frequent, at least not frequent enough to make me want to throw it out of the window. 

But if this not being able to write to it is another symptom of the same buggyness, than it's time to pick up a new one... Can this hardware problem cause the no-permission thing?

---

### Post by hajk on 2005-12-12
Make sure that the mount point /media/hdb1 also has write permission with the command "sudo chmod 777 /media/hdb1", otherwise you'll always get the "...you are not the owner..." message.

Same for /mnt/hdb1, if you're using that non-standard mount point...

---

### Post by psusi on 2005-12-12
Look at the output of dmesg or the contents of /var/log/messages or kern.log for any error messages that might be related.  

If the disk is dieing that might explain it.  You might want to run the badblocks program on it to check it out.  If you happen to dual boot with windows it might be easier to boot up windows and ask it to scan the disk, and check the option to search for and attempt to recover bad sectors.

---

### Post by DFreeze on 2005-12-26
It's been a while since I could try some of the suggestions mentioned here. The file BDisk, the one the faulty Harddisk is mounted upon, is fully 'open': everyone can r/x/w on it.

I tried umask=0000 (four zeros) as well, but that too didn't help. I guess we're at an end here?

The funny thing remains: the disk was making noises with Hoary as well, but I had it mounted in no-time. Never had anything like this...

---

### Post by Zwack on 2005-12-26
I could be wrong, but those "noises" sound like a symptom of hardware problems.

You need to check the filesystem fsck -n /dev/hdb1 should do the job.  If it finds any errors then fsck -a /dev/hdb1 might fix them.  Make sure that you unmount the file system first.

I hope that this helps,

Z

---

### Post by DFreeze on 2006-01-09
I finally fixed the problem regarding these strange write-phenomena. First of all, the clicking noise was hardware related, but not so ominous as I feared. It appeared that the power-connector to the drive had a loose pin-socket, causing frequent power-downs on the drive. 

This has apparently messed up the FAT table so bad, that I couldn't get any normal write-behaviour on it. So I backed up the drive, and made it FAT32 again with gParted. That fixed the problem.

Off course I also fixed the power-connector, so now the system is working again as it should. 

Thanks for all your help. I learn a lot from you guys!

---

