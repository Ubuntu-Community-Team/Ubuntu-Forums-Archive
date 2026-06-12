---
title: "Do not have permissions to write to folder! (Solved)"
date: 2005-10-24
forum: Desktop Environments
---

### Post by yash on 2005-10-24
I have a partition (fat32 31 gig) that i can read files from but I cannot write too.  I have a user account that is not root but it has no permissions that require root access rights. How do i grant my user account all access root power?

Ron

---

### Post by Kyral on 2005-10-24
First off, going with Root Power all the time is not smart (Actually its what Windows does, but thats another rant)

Secondly can you do

```
cat /etc/fstab
```

And paste the output here?

---

### Post by yash on 2005-10-24
all I want right now is to be able to put whatever files I want in my Fat32 partition and be able to read it in both linux and windows.  How do I use "cat /etc/fstab" to gain these access rights?

Ron

---

### Post by Beggar on 2005-10-24
the way to do this is modify your fstab file to mount the drive so that your user account has r/w/x privelages, he just wants to see whats there so he can edit it for you and just give you what to replace it with.

---

### Post by Kyral on 2005-10-24
[QUOTE=yash]all I want right now is to be able to put whatever files I want in my Fat32 partition and be able to read it in both linux and windows.  How do I use "cat /etc/fstab" to gain these access rights?

Ron[/QUOTE]
cat just throws the output of the file to the screen (Don't try it with binary files, it will mess up your terminal)

If you are interested I have a nifty guide to the terminal right at the bottom of my posts :D

---

### Post by aysiu on 2005-10-24
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by yash on 2005-10-26
:???: Not sure if I'm making myself clear.  The situation is that I have a fat32 partition so that both linux and windows can share it.  Now, on the linux end...the File owner and file group for the drive is only root.  Owner has all read, write, and execute while group has read and execute.  My user account is in the group root but it does not have the writting permissions.  I want to edit my user account so that I can write to that drive. 

Is there a command I can type that will add the writting permission to the root group?  :confused:  

:p My goal is to use that drive to download stuff, like music or movies, and write to it....and then still have access to those files in windows. :p

---

### Post by Casey on 2005-10-26
To do this you should edit your fstab. That is why people want you to post the contents of your fstab here (because mucking around with it while not really understanding what you are doing is a recipe for major trouble).

Edit: Open a terminal.  Type "cat /etc/fstab" (without the quotes).

You should get something that looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               reiserfs notail          0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Select that and copy it (using ctrl-shift-c or the right mouse button to select copy) to this thread.  You can wrap it in code tags (the # sign) to make it easy to read.

---

### Post by yash on 2005-10-26
aah..a light has turned on! Ok....here's what it says.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /mnt/wxp        vfat    rw,user,auto
root@ubuntu:/home/ron #

---

### Post by Casey on 2005-10-26
I am not certain that this is right, so make sure you backup your configuration first!
```
sudo cp /etc/fstab /etc/fstab_backup
```
I am getting my information from ubuntuguide.org.

If anything fails, go into failsafe and copy the backup over the modified one (like so):
```
sudo cp /etc/fstab_backup /etc/fstab
```

That said, from the terminal run:
```
sudo gedit /etc/fstab
```

Replace this line:
```
/dev/hda5 /mnt/wxp vfat rw,user,auto
```
with:
```
/dev/hda5       /mnt/wxp  vfat    iocharset=utf8,umask=000   0       0
```

From what I can tell at ubuntu guide, that should mount the partition at bootup and allow all users to read/write.

Please please please make a backup of fstab first!  I do not have a fat32 partition and have no way to test these instructions.

---

### Post by yash on 2005-10-28
Awesome, I made that change to the fstab.  But one little problem...in my attempt to fix it myself before I had this info I unmounted the drive.  I tried doing the remount: 
[INDENT]"sudo mount /dev/hda5 /mnt/wxp -t vfat -o iocharset=utf8,umask=000"[/INDENT]

that doesnt really work.  What do I type to get it to mount again?

Ron:confused:

---

### Post by Kyral on 2005-10-28
a "mount /mnt/wxp" should work now (Sudo it if it doesn't :P)

---

### Post by yash on 2005-10-28
neither work...its says
     wrong fs type, bad option, bad superblock on /dev/hda5,
     missing codepage or other error
     In some cases useful info is found in syslog -try
     dmesg | tail or so

:confused:

---

### Post by Kyral on 2005-10-28
Try this one (Just skimmed the man mount)

/dev/hda5       /mnt/wxp  vfat    umask=0000,uid=1000,gid=1000,rw,user,auto   0       0

Its the "Brute Force" method to tell mount that EVERYONE should have access to this drive ;P

---

### Post by yash on 2005-10-28
haha...it doesnt like that.  It says:
   "Permission denied"

---

### Post by Kyral on 2005-10-28
Where does it say permission denied?
(Console output maybe?)

---

### Post by yash on 2005-10-28
in the root terminal it says, 

 root@ubuntu:/home/ron # /dev/hda5 /mnt/wxp vfat umask=0000,uid=1000,gid=1000,rw,user,auto 0 0
bash: /dev/hda5: Permission denied

---

### Post by Kyral on 2005-10-28
I meant put that in your fstab ;P

---

### Post by yash on 2005-10-28
neat...but it has a floppy drive looking thing in the "Computer" window and it says "Not Mounted"  its called "254M Hard Drive"  shouldn't be that small...looks like a swap drive or something.  But the drive should say at least 27 gigs....

---

### Post by Kyral on 2005-10-28
Didja replace this line

/dev/hda5       /mnt/wxp  vfat    iocharset=utf8,umask=000   0       0

with the one I gave you?

Maybe we need to see the current state of the fstab...and the output from sudo fdisk -l.

*sigh* This is why I prefer to do tech support in person ;P

---

### Post by yash on 2005-10-28
root@ubuntu:/home/ron # fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         625     5020281    7  HPFS/NTFS
/dev/hda2            1291        4864    28708155    f  W95 Ext'd (LBA)
/dev/hda3             685        1290     4867695   83  Linux
/dev/hda5            1291        1321      248976   82  Linux swap / Solaris
/dev/hda6            1322        4864    28459116    b  W95 FAT32

Partition table entries are not in disk order
root@ubuntu:/home/ron # cat fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /mnt/wxp        vfat    rw,user,auto
root@ubuntu:/home/ron #
root@ubuntu:/home/ron #

---

### Post by Kyral on 2005-10-28
Yeeea...thats why its small. /dev/hda5 IS the Swap drive. Where we are helping you, replace hda5 with hda6 ;P

So the line I gave you SHOULD look like
 /dev/hda6/mnt/wxp  vfat    umask=0000,uid=1000,gid=1000,rw,user,auto   0       0

and also change the instance of hda6 in your current fstab to hda5.

Mind giving the fstab after you change it. Just wanna make sure its right ;P

---

### Post by yash on 2005-10-28
[COLOR="red"]This is what i see...[/COLOR]
root@ubuntu:/home/ron # cat fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /mnt/wxp        vfat    rw,user,auto

[COLOR="Red"]but when i do the  sudo gedit /etc/fstab it shows this...[/COLOR]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda6	/mnt/wxp	vfat	umask=0000,uid=1000,rw,user,auto 0 0

---

### Post by Kyral on 2005-10-28
Thats because when you did a "cat fstab" you cat'd the file in your home directory called "fstab", not /etc/fstab ;P

---

### Post by yash on 2005-10-28
so is everything ok?  i see that it put the 29G Hard Drive in my "Computer" window...but when i right click to select "Mount" it says, "Unable to mount the selected volume.  Mount: according to mtab, none is already mounted on none.  Mount failed"

---

### Post by Kyral on 2005-10-28
Change this line
 /dev/hda6       none            swap    sw              0       0

to this
/dev/hda5 none swap sw 0 0

May have to pull a reboot for this one to take effect since you are changing where it sees the swap drive.

*Uhoh....this might be a problem. If the system trying to use the FAT32 as swap......then data might have been deleted or changed because to the system Swap == RAM*

---

### Post by yash on 2005-10-28
:: :D Bows down in humbleness and kisses your feet! :D ::
hahaha..it worked!!! it worked!!! Thanks! Your a genious! :KS 

I'm glad i had a chance to go through all that..i feel i've actually learned a bit of linux now ;)

---

### Post by Kyral on 2005-10-28
Whew, I'm glad I was wrong about data on that drive being turned into Swap food ;P

Now stuff will seem easy, until you decide to play with the Kernel (Which after the first time you do it is quite fun :D)

---

