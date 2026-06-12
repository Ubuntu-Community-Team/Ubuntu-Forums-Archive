---
title: "Need a little patitioning advice for fresh install"
date: 2012-10-17
forum: Desktop Environments
---

### Post by Grimace78 on 2012-10-17
I am running a duel boot(win 7 64/ubuntu 64), and have run into some issues trying to get the most out of both operating systems with my hardware environment.

Hard drive array is as follows:
1 120gb  intel 520 SSD 
2 1tb HDDs set up in fake raid (900gb raid 0/ 400ish gb in raid 1)

Here is the problem. I have a gigabyte z68 mobo, and to get the most out of it in windows 7 (EZ smart response from intel) it needs part of the ssd to work (I gave it 20gb with great results: 1268 novabench score, avg is 762). 

I gave the rest of the ssd drive to Ubuntu, because I like it a lot more than windows. The problem is when I reinstalled ubuntu onto the ssd, intel parrallel studio doesn't have the space it needs to install into the /opt/intel/ directory (needs about 2 more gigs of space). 

I was thinking I could just specify with the advanced partitioning tool that the opt directory has enough space, but that's pretty much me just guessing/making assumptions. 

Another issue is that I am really not all that impressed with the Ubuntu backup, and have an acronis program that will back it up correctly in windows to the raid 1 partion, but it (home director 11) says that it doesn't support file ext 4. 

I don't know anything about how to use advanced partitioning in file ext 3, which is supported. I also don't know how well file ext 3 works.


Any chance someone could give me the skinny on these issues/possibly some advice?

---

### Post by oldfred on 2012-10-17
I do not know RAID and as I understand you gave 100GB to Ubuntu and Intel software still does not fit?

I installed / (root) including /home into my 60GB SSD with another install of Ubuntu or two / of about 30GB. Including /home of about 2GB I use 9GB total of the 30GB.  But I keep all data including some of the hidden data folders in /home on my rotating drive. I just do not have RAID.

Post these.

sudo parted /dev/sda unit s print
df -h

You may be an exception, but this is basically what I prefer. Except Herman does not use a separate swap partition now either.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

And I believe every drive should be bootable, except I have Ubuntu on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by Grimace78 on 2012-10-17
> **oldfred said:**
> I do not know RAID and as I understand you gave 100GB to Ubuntu and Intel software still does not fit?

I installed / (root) including /home into my 60GB SSD with another install of Ubuntu or two / of about 30GB. Including /home of about 2GB I use 9GB total of the 30GB.  But I keep all data including some of the hidden data folders in /home on my rotating drive. I just do not have RAID.

Post these.

sudo parted /dev/sda unit s print
df -h

You may be an exception, but this is basically what I prefer. Except Herman does not use a separate swap partition now either.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

And I believe every drive should be bootable, except I have Ubuntu on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I couldn't run the command you gave, because something went wrong with the reinstall I tried in ext 3. It turned out to be pretty pointless anyway because it would only have enabled Disk Director to resize it's partitions (supposedly). If I get it right the first time, I won't need that.

This is the hard drive array that I have to work with:

[IMG]http://i1130.photobucket.com/albums/m525/dgrimes1/harddrivearray.png[/IMG]

As to there not being enough room, all I know is that Parrellel Studio installed fine before I shrunk the SSD partition it was on by 20 GB. Afterwards, it said in the terminal that it need an additional 2.2 ish gb to install.

In advanced partitioning, these were my choices.

bootloader: Intel SSD
boot: 600 mb
root: 15 GB
home: the rest of the drive
swap: 16 GB on my spare HDD

I realize that the boot and root are excessivley large, but I was following an advanced partitioning guide that recommended those amounts for growth of the system later on. 

My long term goal with Ubuntu is to build a custom kernel specifically for my system. This is partly for the new challenge, and quite a bit for the incompatibilities that I run into with a gigabyte mobo. It has a realtech lan chip, that for the life of me I can't find compatible drivers for (which means my wireless pci card won't work), etc. I want to transition into programming anyways so I figured it would be a good project.

If you could give me some advice on how to make this work while keeping the 20GB SSD partition for windows 7 I would be very appreciative.

Edit: I didn't have the time yet to look through the info on the links and appoligize for that. Just didn't want to take too long to respond and have been extremely busy.

---

### Post by oldfred on 2012-10-17
The 87 GB should be huge for / (root). I would not have a separate /boot. And if you really are going to keep all data on other partitions I might leave /home inside the / partition and link or bind other partitions with data into /home.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by BelJoost on 2012-10-19
In the past I have used gparted (it's on the e.g. systemrescuecd) to give windows some extra space. Or to strip some space from it to create free space for an ubuntu install.

You could give that a try.

I always use partimage or clonezilla to make a copy of the disc or partition(s) in question. If I remember it right, partimage does not support ext4. You mention ext3, so I guess your safe.

---

### Post by Grimace78 on 2012-10-20
> **oldfred said:**
> The 87 GB should be huge for / (root). I would not have a separate /boot. And if you really are going to keep all data on other partitions I might leave /home inside the / partition and link or bind other partitions with data into /home.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

> **BelJoost said:**
> In the past I have used gparted (it's on the e.g. systemrescuecd) to give windows some extra space. Or to strip some space from it to create free space for an ubuntu install.

You could give that a try.

I always use partimage or clonezilla to make a copy of the disc or partition(s) in question. If I remember it right, partimage does not support ext4. You mention ext3, so I guess your safe.

Well, it took a while, and I ran into some other snags I'm just gonna blame on the ADD (LOL), but I'm up and running and apparently have plenty of space. Thank you very much olfred :). BelJoost, if I happen to run into this problem again, I'll be sure and check that out. Thank you as well.

---

