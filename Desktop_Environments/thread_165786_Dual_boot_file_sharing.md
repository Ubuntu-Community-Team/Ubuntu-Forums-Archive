---
title: "Dual boot file sharing"
date: 2006-04-25
forum: Desktop Environments
---

### Post by johnkennethhughes on 2006-04-25
I would like to set up my computer to dual boot with Ubuntu and Windows (nice and simple: all default settings) and would like to be able to access files from Ubuntu in Windows and files from Windows in Ubuntu. Looking around the forums, there seem to various solutions to this including adding extra partitions with different file systems and using Windows drivers to mount the Ubuntu partition etc. As far as I understand, mounting partitions like that would compromise security (being able to access anyone's files).

Basically, I'm getting a little confused. So what is the easiest/ best way of sharing files between the two operating systems?

---

### Post by Sef on 2006-04-25
You need to set up either a FAT32 or ext 2 partition.   Both Windows and Linux can read and write to those partitions.

So there would be a set up similar to this:

Patition 1: XP           - NTFS
Partition 2: Shared  - FAT32
Partition 3: Ubuntu  - Root
Partition 4: Home    - Ext3 or Reiserfs
Partition 5: Swap     - swap

Note: At least one would be an extended partition and not a primary.  There can only be 4 primary partitions.

---

### Post by jazzmuzik on 2006-04-25
As Sef says, create a FAT32 partition. That will be the shared partition. By default Ubuntu only gives read access to windows partitions, but you can change that in the /etc/fstab file.

---

### Post by louis_nichols on 2006-04-25
I would do something else, more surprising, perhaps. I would set the shared partition as ext2. Linux wll obviously support it natively. then, under win, you can use the driver [here]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")(read-only) or [here]("http://ext2fsd.sourceforge.net/#ext2fsd")(read-write).

the reason I'm sying this is that fat32 doesn't support files larger than about 3 gigs, so no dvd images and stuff.

---

### Post by 999.michael on 2006-04-25
have you tried visiting [http://www.fs-driver.org]("http://www.fs-driver.org") it lets you see + edit linux ext2 partitions in windows

---

### Post by spade_shark on 2006-04-26
I would do similar to Sef.  I create a single fat32 part. and use for common storage for all operating systems.  As of now, any windows viruses should not jump into linux.  

How about getting a usb 2gb flash drive?  Those do come in handy. :)

---

### Post by johnkennethhughes on 2006-04-26
Wow, thanks for all the input everyone. It's been very helpful. As the simplest and cheapest option, I'm going to start by trying out a FAT32 partition. Thanks again.

---

### Post by johnkennethhughes on 2006-04-26
Okay - I've been trying to use GParted on the Breezy live CD to add a FAT32 partition to the disk and it won't let me, saying that some of the partitions are still mounted. Looks like the live CD automatically mounts the swap partition on the hard disk when it boots. I've tried using the GParted live CD instead, but that refuses to boot, giving the message:

> Unknown keyword in config file
boot:
Could not find kernal image: livecd
boot:

So I'm not having much luck! Any suggestions?

---

### Post by Ramses de Norre on 2006-04-26
Can you just unmount the mounted partitions? For the swap use sudo swapoff -a

---

### Post by johnkennethhughes on 2006-04-26
Tried it. Still comes up with an error (although this time it doesn't say what the error is) and doesn't change any of the partitions.

---

### Post by Ramses de Norre on 2006-04-26
It doesn't say what the error is? What does it do then?

---

### Post by johnkennethhughes on 2006-04-27
Using the Breezy live CD and GParted:

After pressing the 'apply' button and waiting a few minutes, it brings up a window entitled 'Error' or something silimar, with nothing in the window except a 'cancel' button. When I press that, it returns me to the GParted window and the partitions appear to be exactly the same as they were before I changed anything.

---

### Post by LostBear on 2006-04-28
the easiest way is to use a tool such as partionmagic, this will let u resize the windows partion without destroying the data on it. leave the space after it blank...nothing...zilch....no file system. dead. 

then run the breezy INSTALL cd and it will auto partion the empty space at the end of the drive. u can either add your fat32/ext shared partion for swapping stuff between the oses, or complete the install, boot back in to windows and use partition magic to resize the partions. if your going to do this, id reccommend making the swap partition twice the size it reccomends, then u can halve it with partion magic and create your fat32 partion at the end of the drive for swapping files between ubuntu. this ust keeps things tudy, as the fat32 partion will be at the end of the drive and not buried inbetween the linux partions.

it sounds long winded but its not really.  can be done in a bout an hour on a modern pc. 

Hope this helps.

---

### Post by johnkennethhughes on 2006-04-28
Doesn't Partition Magic cost money? All I need to be able to do is run the Ubuntu Live CD without it automatically mounting the swap partition on the hard disk. When GParted is included on the Live CD, surely actually using GParted should be easy?

---

### Post by LostBear on 2006-04-28
you can use a trial version. 

I have never tried to use the live cd to partion the disks. I merely stated the way in which i got a dual boot going and was able to share files between the two operating systems.

---

### Post by LostBear on 2006-04-28
Hmm my bad...seems partition magic is now owned by Symantec, and i cant seem to find a trial version of it.

---

### Post by LostBear on 2006-04-28
ok...you could give this a go

[http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

---

### Post by LostBear on 2006-04-28
failing that try typing "hiren" in a bit torrent search engine

---

