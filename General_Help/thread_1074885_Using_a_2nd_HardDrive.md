---
title: "Using a 2nd HardDrive"
date: 2009-02-19
forum: General Help
---

### Post by unplugged23 on 2009-02-19
Hey there,

 I was just wondering is someone would be willing to help me with an issue I am having with a hard drive. I have a second hard drive in my computer with nothing on it, which I just formatted to Ext 3. I just wanted to use this hard drive to store things like documents, music and video. I tried to add a file to the hard drive, and it told me I didn't have permission. SO not knowing what to do I just re-formatted it and tried again. Now I'm getting an error message that says "cannot mount volume. unable to mount volume" then when I click on the more details button "mount_point cannout contain the following characters: newline, G_DIR_SEPERATOR (usually /)" Any suggestions? Thanks in advance. :D

---

### Post by taurus on 2009-02-19
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```
Basically, you want to add an entry in /etc/fstab for your second harddrive so it would be mounted automatically each time you boot.  And if it is an ext3 filesystem, then you can change the ownership of the mount point of that harddrive from root to your login name so you can write to it anytime you want.

---

### Post by unplugged23 on 2009-02-19
Thanks! Now as I forgot to mention and I'm sure shows in the following results, I have my boot partition on this drive. This shouldn't cause any problems right?

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92bc92bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          99      795186   83  Linux
/dev/sda2             100        4865    38282895   83  Linux

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9454    75939223+  83  Linux
/dev/sdb2            9455        9726     2184840   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1357     7783940    b  W9




/dev/sda1: UUID="2c3fba6c-f6c3-4456-a641-bbd84f2a72de" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="239f45d6-2d27-4d50-a400-72b0e9ddb51b" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="11e0e02e-7a39-4ce5-b684-2dc07d13773e" 
/dev/sda2: UUID="c89f8696-18f4-46c3-b33f-db6a5e41f4e3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="IZZY" UUID="3141-5926" TYPE="vfat" 




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=239f45d6-2d27-4d50-a400-72b0e9ddb51b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=11e0e02e-7a39-4ce5-b684-2dc07d13773e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              72G   13G   56G  19% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  220K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  992K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc1             7.5G  7.3G  137M  99% /media/IZZY




uid=1000(izzy) gid=1000(izzy) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(izzy)











```

Thanks again for the help! :D

---

### Post by taurus on 2009-02-19
So you want to add both /dev/sda1 & /dev/sda2 so you can write to them.  Or do you want to remove both, /dev/sda1 & /dev/sda2, and create one partition, /dev/sda1, that takes up the whole disk space?

I assume you want to leave /dev/sda1 & /dev/sda2 the way they are.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

UUID=2c3fba6c-f6c3-4456-a641-bbd84f2a72de   /media/sda1   ext3   defaults   0   2
UUID=c89f8696-18f4-46c3-b33f-db6a5e41f4e3   /media/sda2   ext3   defaults   0   2
```
Save it and close down gedit editing windows.  Now, create those two new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda2
sudo mount -a
df -h
```
At this point, you want to change the ownership of /media/sda1 & /dev/sda2 from root to your login name, izzy, so you can write to them anytime you want.  Just run

```
sudo chown -R izzy:izzy /media/sda1
sudo chown -R izzy:izzy /media/sda2
ls -la /media
```

---

### Post by unplugged23 on 2009-02-19
Thanks A lot! Worked Like a Charm! :D

Would someone mind telling me how to mark the thread solved???

---

### Post by taurus on 2009-02-19
Here you go.

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

### Post by unplugged23 on 2009-02-19
Alright, thanks!

---

### Post by utherpendragonfly on 2009-02-19
> **taurus said:**
> Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```
Basically, you want to add an entry in /etc/fstab for your second harddrive so it would be mounted automatically each time you boot.  And if it is an ext3 filesystem, then you can change the ownership of the mount point of that harddrive from root to your login name so you can write to it anytime you want.

I'm having the same problem trying to mount a 2nd internal HD. I've tried following some advice from this forum and must have screwed something up, (actually I tried several techniques, which all seemed to be saying to do something different) with no luck. And now when I try to reformat the HD as Ext 3 with Gparted, I can't even do that. Here is the result below. Can anyone help?

---

### Post by taurus on 2009-02-19
What app is that?  I don't believe it's gparted.

Can you post the outputs of those commands while you are in Ubuntu?

---

### Post by utherpendragonfly on 2009-02-19
I used System>Administration>Partition Editor, which is GParted to try an format sdb.

Here are the CL results:

davey@davey-desktop:~$ sudo fdisk -l
[sudo] password for davey: 

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa9d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90446   726507463+  83  Linux
/dev/sda2           90447       91201     6064537+   5  Extended
/dev/sda5           90447       91201     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000730b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
davey@davey-desktop:~$ sudo blkid
/dev/sda1: UUID="9eea5094-9713-461d-bb0d-d0042cc7fb71" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="8d320dc5-7e87-4938-afe0-84bfacaf6b7b" 
/dev/sdb1: UUID="30886536-1c0c-45bf-b723-5775e1e62a28" TYPE="ext3" SEC_TYPE="ext2" LABEL="Backup" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb5: TYPE="swap" UUID="72427d47-2dd5-4390-a4fb-7cdc18a886cd" 
/dev/sdb2: LABEL="Storage" UUID="2dd3510d-5109-4b07-918f-a1aa787b016a" SEC_TYPE="ext2" TYPE="ext3" 
davey@davey-desktop:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
davey@davey-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             682G  120G  529G  19% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  124K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.7M 1010M   1% /dev
tmpfs                1013M  1.3M 1011M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-11-generic/volatile
davey@davey-desktop:~$ id
uid=1000(davey) gid=1000(davey) groups=4(adm),20(dialout),21(fax),24(cdrom),29(audio),44(video),46(plugdev),102(netdev),105(scanner),107(fuse),113(lpadmin),114(pulse),115(pulse-access),116(pulse-rt),122(admin),124(sambashare),1000(davey)
davey@davey-desktop:~$

---

### Post by utherpendragonfly on 2009-02-19
Sorry it took so long to get back...

---

### Post by taurus on 2009-02-19
See if you can actually mount it by hand from a terminal first.

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```
Do you see /dev/sdb1 mounted to /media/sdb1 from the output of the last command?

---

### Post by utherpendragonfly on 2009-02-19
Here's what I get:

davey@davey-desktop:~$ sudo mkdir /media/sdb1
davey@davey-desktop:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: special device /dev/sdb1 does not exist
davey@davey-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             682G  120G  529G  19% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  124K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.7M 1010M   1% /dev
tmpfs                1013M  1.3M 1011M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-11-generic/volatile
davey@davey-desktop:~$ 

...I forgot to mention, when I was unable to gain access to the drive I tried installing Kubuntu on it yesterday, but was unable to access grub for Kubuntu or copy anything from it. I think I've really made a mess of the mount points and everything!

---

### Post by taurus on 2009-02-19
Start System -> Administration -> Partition Editor again and click the tab on the right to point to /dev/sdb.  Now, delete whatever on it and create a new partition, /dev/sdb1, that takes up the whole disk space and format it to ext3.  Save it and then see if you can mount it by hand from a terminal this time.

---

### Post by utherpendragonfly on 2009-02-19
I'm in Partition editor. I think when I tried to delete the whole partition sdb earlier I did NOT click Apply. I'm doing it again. What should I fill in for "Label"? Does it matter?

---

### Post by taurus on 2009-02-19
You can call it whatever you want, second_drive.

---

### Post by utherpendragonfly on 2009-02-19
I tried it again, called it "HD2" and got the same error message as before;
mkfs.ext3 -L "HD2" /dev/sdb1

---

### Post by utherpendragonfly on 2009-02-19
The result in GParted is Partition: dev/sdb1  Filesystem Unknown

---

### Post by taurus on 2009-02-19
Close down gparted.  From a terminal, run

```
sudo cfdisk /dev/sdb
```
Post a screenshot of that window.

---

### Post by utherpendragonfly on 2009-02-19
Here's what I got. Thank you for your time & patience!

---

### Post by taurus on 2009-02-19
Use the arrow to highlight the Type and hit Return.  Then, enter 83 (linux ext3) for that partition, /dev/sdb1.  Now, highlight the Write and hit Return to write it to disk.  Hit Quite to exit.  At this point, you need to format it.

```
sudo mke2fs -j /dev/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by utherpendragonfly on 2009-02-19
I did what you said and quit. 
Then opened GParted again and tried formating sdb1 as Ext3 again, but got back the same error message!
In terminal I got:

davey@davey-desktop:~$ sudo cfdisk /dev/sdb
[sudo] password for davey: 

Disk has been changed.

WARNING: If you have created or modified any
DOS 6.x partitions, please see the cfdisk manual
page for additional information.

---

### Post by utherpendragonfly on 2009-02-19
Wait.. I didn't enetr terminal commands!!! sorry. trying that now...

---

### Post by taurus on 2009-02-19
Please format it from a terminal with the _mke2fs_ command in my previous post.

---

### Post by utherpendragonfly on 2009-02-19
Here is the complete;

Disk has been changed.

WARNING: If you have created or modified any
DOS 6.x partitions, please see the cfdisk manual
page for additional information.
davey@davey-desktop:~$ sudo mke2fs -j /dev/sdb1
[sudo] password for davey: 
mke2fs 1.41.3 (12-Oct-2008)
Could not stat /dev/sdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
davey@davey-desktop:~$ sudo mount -t ext3 /dev/sbd1 /media/sdb1
mount: special device /dev/sbd1 does not exist
davey@davey-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             682G  120G  529G  19% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  124K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.7M 1010M   1% /dev
tmpfs                1013M  1.3M 1011M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-11-generic/volatile
davey@davey-desktop:~$

---

### Post by taurus on 2009-02-19
After you run this command again from a terminal, **sudo cfdisk /dev/sdb**, what does the screen look now?

---

### Post by utherpendragonfly on 2009-02-19
In Nautilus I see: /dev/sbd - but no sbd1
and there is a folder  /media/sbd1

---

### Post by taurus on 2009-02-19
Run this command again and post the screenshot of it.

```
sudo cfdisk /dev/sdb
```

---

### Post by utherpendragonfly on 2009-02-19
This doesn't look good...

---

### Post by taurus on 2009-02-19
Maybe you want to reboot.  Then, open a terminal and see if your second drive, /dev/sdb, is still there.

```
sudo fdisk -l
```
Also, while the machine is rebooting, go into the BIOS and make sure the BIOS is happy with all the harddrives on your machine.

---

### Post by utherpendragonfly on 2009-02-19
OK. It's getting late, and I should probably let you go. How about if I post the results back here tomorrow? I really appreciate all your effort.

---

### Post by utherpendragonfly on 2009-02-19
Bios shows both HDs. I saw there was a private message, but the popup blocker prevented it! I changed the preferences in Firefox, but no luck!

Here's my last post for tonight:

davey@davey-desktop:~$ sudo fdisk -l
[sudo] password for davey: 

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa9d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90446   726507463+  83  Linux
/dev/sda2           90447       91201     6064537+   5  Extended
/dev/sda5           90447       91201     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000730b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

---

### Post by taurus on 2009-02-19
```
sudo mke2fs -j /dev/sdb1
```

p.s.  And I am out of here...

---

### Post by utherpendragonfly on 2009-02-20
Here is latest screenshot on Friday:

---

### Post by chipppy on 2009-02-23
I am trying to follow this thread to add in a 2nd automount HDD aswell
At the bottom is the output from the commands at theI start of this thread
I am new to Linux and I am trying to setup a Mythbunutu box.
the 2nd HDD is to increase the storage space for movies.

I have edited the fstab to look like the following.  (The # is to keep it as a comment for the moment until I am sure things are correct)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7ddfc935-8b71-41f7-9655-3c6d47860d76 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=3f968843-e1e6-43e8-a8ff-de2ca1f4b4f7 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=d4c916b3-0e43-4a4e-b8b6-36abf1afd0f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/sdb1 LABEL="Movies" 
#UUID="882c7288-47f6-4e23-b171-8727e67cfef0 /var/lib   	  xfs	   defaults	   0	  2

The idea is to add in /dev/sdb1 to store my movies on.  I have mounted in at /var/lib the same as mythbuntu automagically did.  The same reason forthe 'xfs' format
Is this the right way to set this up?


I also have a second problem here.
I want to increase the size of my 'ext3' boot partion to 50GB as it is curently only 11GB and getting full of games.
How do i do this?
In partion editor I cannot change the size of this partion /dev/sda1.  I think that I need to unmount all the sda*'s before i can change thier size but i am not sure and I also dont know how to do this as it wont let me unmount anything in sda.
How toI increase the size of the sda1 partion?

Cheers
chipppy

chipppy@chipppy:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8e47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       60801   476664615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584       60801   475668553+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b842f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
chipppy@chipppy:~$ sudo blkid
/dev/sda1: UUID="7ddfc935-8b71-41f7-9655-3c6d47860d76" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d4c916b3-0e43-4a4e-b8b6-36abf1afd0f0" 
/dev/sda6: UUID="3f968843-e1e6-43e8-a8ff-de2ca1f4b4f7" TYPE="xfs" 
/dev/sdb1: LABEL="Movies" UUID="882c7288-47f6-4e23-b171-8727e67cfef0" TYPE="xfs" 
chipppy@chipppy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7ddfc935-8b71-41f7-9655-3c6d47860d76 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=3f968843-e1e6-43e8-a8ff-de2ca1f4b4f7 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=d4c916b3-0e43-4a4e-b8b6-36abf1afd0f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
chipppy@chipppy:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.6G  6.9G  35% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  336K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  3.0M  2.0G   1% /dev
tmpfs                 2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             454G   11G  444G   3% /var/lib
chipppy@chipppy:~$ id
uid=1000(chipppy) gid=1000(chipppy) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(mythtv),115(lpadmin),117(sambashare),123(admin),1000(chipppy)
chipppy@chipppy:~$ gksudo gedit /etc/fstab

---

