---
title: "Ext4, Grub, file 15 error, and UUID update"
date: 2009-05-18
forum: General Help
---

### Post by VMC on 2009-05-18
I installed Jaunty using file system Ext4, Everything was fine...

Somewhere along the way, Grub failed. I tried everything I knew. Googled for days. Only to re-install Jaunty again.

Determined not to let this happen again, I tried to find a good backup method:

Tar is to time consuming.
Partimage doesn't support Ext4.
Clonezilla to the rescue;I thought. Yes it does backup Ext4. The only problem I found out is that once imaged you must restore to the same partition number. So you can't image sda3, for example and restore to say sdb1.

In come FSArchiver to the rescue;I thought. It's a great and fairly fast backup and very fast restore. The only trouble I'm having is it constantly finds crc errors on its own image. Maybe 1, maybe 3. There's no way that I can backup up a partition and then check that all the files are intact, like you can with Acronis True Image or Partimage "Simulation". I tried to send it to /dev/null, but of course that's not a block device. Only way to find out if FSArchiver has any errors is to restore the image.

I kept hearing about grub boot extenders, or an updated grub. When I tried all the tine distros - Part Magic, Knoppix, etc. Grub would fail to find the Ext4 grub stage1.

Finally in steps "Super Grub Disk" version 9795. It works with Ext4. All you need to do is "tab","c", for the grub> prompt. Then the famous find /boot/grub/stage1, finds Ext4 brug information!

Now comes another strange happening. In all of this and before I found that SGD would work I manage to use Clonezilla to restore my Jaunty partition which is on Partition#3, to a attached USB hard drive. I had to create three partitions just to restore to P3. Clonezilla also has problems with grub and errors out complaining about grub. So I also used FSArchiver to restore P3 of Jaunty to the USB disk P1. That worked, albeit the crc error it found along the way.

So now with SGD in hand I removed all HD's and installed that USD disk as a normal HD. To my surprise it booted up! I'm still in the dark as to how grub got installed. P1 & P3 both have Jaunty installed. One from Clonezilla's resote the other from FSArchiver. The problem is both have the same UUID number. How to update those partitions? Googling found a couple of ideas:

UUID probelm...

mc@vmc-desktop:~$ **sudo blkid**
/dev/sda1: UUID="[COLOR="Red"]**1d435768-6649-4d4f-b3b2-ff318219e5c7**[/COLOR]" TYPE="ext4" 
/dev/sda2: UUID="c9220f6e-2481-4ac5-b023-1e985b68068c" TYPE="ext4" 
/dev/sda3: UUID="**[COLOR="Red"]1d435768-6649-4d4f-b3b2-ff318219e5c7[/COLOR]**" TYPE="ext4" 
vmc@vmc-desktop:~$ **sudo partprobe**
vmc@vmc-desktop:~$** sudo blkid**
/dev/sda1: UUID="1d435768-6649-4d4f-b3b2-ff318219e5c7" TYPE="ext4" 
/dev/sda2: UUID="c9220f6e-2481-4ac5-b023-1e985b68068c" TYPE="ext4" 
/dev/sda3: UUID="1d435768-6649-4d4f-b3b2-ff318219e5c7" TYPE="ext4" 
vmc@vmc-desktop:~$ **sudo /etc/init.d/udev restart**
 * Stopping kernel event manager...                                      [ OK ] 
 * Starting kernel event manager...                                      [ OK ] 
vmc@vmc-desktop:~$ **sudo blkid**
/dev/sda1: UUID="[COLOR="Red"]**1d435768-6649-4d4f-b3b2-ff318219e5c7**[/COLOR]" TYPE="ext4" 
/dev/sda2: UUID="c9220f6e-2481-4ac5-b023-1e985b68068c" TYPE="ext4" 
/dev/sda3: UUID="[COLOR="Red"]**1d435768-6649-4d4f-b3b2-ff318219e5c7**[/COLOR]" TYPE="ext4" 

As you can see, the UUID's never change. They are the same.

Any ideas on that one?

---

### Post by logos34 on 2009-05-18
when you image/clone a partition or the entire disk, it copies EVERYTHING--even the UUIDs.

you can manually change the UUIDs to avoid confusion or for security reasons with:
[B]
sudo tune2fs -U random /dev/sda3[/B]

(tune2fs is part of e2fsprogs pkg.  recent versions support ext4)

then edit your menu.lst and fstab files


> Finally in steps "Super Grub Disk" version 9795. It works with Ext4. 

hmm, didn't know that.

As for tools to image, there's also **dd** command--one of the most basic, elegant linux commands and hardly anyone ever uses it or is even aware of it:

> 
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
Examples: duplicate one hard disk partition to another hard disk:
Code:

**dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror**

sda2 and sdb2 are partitions. You want to duplicate sda2 to sdb2. If sdb2 doesn't exist, dd will start at the beginning of the disk, and create it. Be careful with order of if and of. You can write a blank disk to a good disk if you get confused. If you duplicate a smaller partition to a larger one the larger one, using dd, the larger one will now be formatted the same as the smaller one, and there won't be any space left on the drive. The way around this is to use

only thing is, it copies even unused sectors, so it takes a little longer

Or to make a compressed (.gz) backup of a partition:

To create a zipped hard drive backup image:

> # **dd if=/dev/hda2 | gzip > /mnt/hdb1/system_drive_backup.img.gz**

Here dd is making an image of the first harddrive, and piping it through the gzip compression program. The compressed image is then placed in a file on a separate drive. To reverse the process:

# **gzip -dc /mnt/hdb1/system_drive_backup.img.gz | dd of=/dev/hda2**

Here, gzip is decompressing (the -d switch) the file, sending the results to stdout (the -c switch), which are piped to dd, and then written to /dev/hda2.

Hope that helps

enjoy ubuntu

---

### Post by albinootje on 2009-05-18
> **VMC said:**
> 
Clonezilla to the rescue;I thought. Yes it does backup Ext4. The only problem I found out is that once imaged you must restore to the same partition number. So you can't image sda3, for example and restore to say sdb1.

You actually can... by editing the text files that are produced after making the images. 
I found out about this after I made a CloneZilla image from /dev/hda, and wanted to restore it on a machine which showed /dev/sda, or something like that.

I could replace every instance of /dev/hda* (e.g. /dev/hda1,/dev/hda2 etc.) with /dev/sda* in those text files, and got the restoring working.
> 
As you can see, the UUID's never change. They are the same.

What is exactly your question about this ? 
What do you mean with "update" the UUIDs ?

Perhaps the comments here are useful ?
[http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html](http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html)

---

### Post by albinootje on 2009-05-18
By the way, interesting that you mention FSArchiver, yesterday I read an article about the new SystemRescueCd which has FSArchiver included :
[http://www.sysresccd.org/news/2009/05/12/systemrescuecd-120-released/](http://www.sysresccd.org/news/2009/05/12/systemrescuecd-120-released/)

Thanks for mentioning that, I'd like to try/test FSArchiver soonish. :)

---

### Post by VMC on 2009-05-18
> **albinootje said:**
> You actually can... by editing the text files that are produced after making the images. 
I found out about this after I made a CloneZilla image from /dev/hda, and wanted to restore it on a machine which showed /dev/sda, or something like that.

I could replace every instance of /dev/hda* (e.g. /dev/hda1,/dev/hda2 etc.) with /dev/sda* in those text files, and got the restoring working.
 Are you kidding me?! I only went as far as changing the "parts" file to reflect the new hard drive. That didn't work. Can you explain further. Here is the output of the saved image:
2009-05-13-18-img/Info-dmi.txt
2009-05-13-18-img/Info-lshw.txt
2009-05-13-18-img/Info-packages.txt
2009-05-13-18-img/parts
2009-05-13-18-img/sda-chs.sf
2009-05-13-18-img/sda-hidden-data-after-mbr
2009-05-13-18-img/sda-mbr
2009-05-13-18-img/sda-pt.parted
2009-05-13-18-img/sda-pt.sf
2009-05-13-18-img/sda3.ext4-ptcl-img.gz.aa

Which ones exactly did you change? Thank you. Also , did you uncheck the restore the grub before the restore? Thanks.

Edit: So I would remove the "sda" above file to say "sdc". How about the data inside any of them like "parts" file?

---

### Post by albinootje on 2009-05-19
> **VMC said:**
>  Which ones exactly did you change?

Okay, I've reproduced what I've used some months ago.

First I made two different disks in VirtualBox using Clonezilla (Command prompt used, with VB-hotkey-F2).
Then I made a clone image from /dev/hda.
Then with "grep" I've searched for "hda" within the text files, and replaced all that, except in the Info-* files, with "hdb".
After that I've renamed all the hda in the file names into hdb.

In your case a few files would look like this, e.g. :
```

2009-05-13-18-img/sdb-chs.sf
2009-05-13-18-img/sdb-hidden-data-after-mbr

```
After that I've restored the saved /dev/hda2 partition on /dev/hdb2.
And in this test I haven't bothered with Grub, as I used some empty virtual disks from scratch.

See attached screenshots for a little bit more.

---

### Post by VMC on 2009-05-20
It appears your saving to different drives and NOT to different partitions. I can save to different drives or drive numbers ok, but not to different partition numbers:

Sda3 > Sdb3 Works

Sda3 > Sdb1 Fails

---

