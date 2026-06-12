---
title: "Ubuntu 64bit and MS Partitions"
date: 2010-12-24
forum: Desktop Environments
---

### Post by HappyLinux on 2010-12-24
I don't know if this has been posted by someone else, or whether I've put things in the correct section, so I do apologise in advance.

When my new computer arrives, and presuming I can get Ubuntu 10.10 to run on it, I need to know a small piece of information.

All being well, I'll be dual-booting Ubuntu with Win7 HP 64bit.

I currently have 2 USB hard drives, both 500GB in size, and both currently formatted as FAT32. On my current system which has Vista HP 32bit, it says that I can format the drives as either NTFS or exFAT.

The thing is, Win7 for some reason doesn't to mount USB HDDs which are formatted as FAT32. It tends to demand that you reformat the HDD. Some fun that is when you have both drives half full with files, etc. You can get round it by going through Win7's system settings, or pre-formatting the drives as NTFS.

In this case, for the use in Ubuntu, I know that it's got read/write for FAT32, but what about NTFS and exFAT?

I've been googling this matter, but it's a bit confusing. I'm no Linux pro, more like a beginner (not an absolute beginner).

From what I gather, there's NTFS-3G from Tuxera [http://www.tuxera.com/community/ntfs-3g-download/]("http://www.tuxera.com/community/ntfs-3g-download/") and a page from Ubuntu themselves [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions").

However, I cannot find any info for 64bit Ubuntu.

Can anyone clarify what I would need to do, as I would like to use both USB HDDs on both Win7 and Ubuntu.

---

### Post by oldfred on 2010-12-24
I do not recommend FAT anymore unless you have a device that requires it. It is fine for small memory cards where your camera or other device has to have it. Small devices also do not need the journal that NTFS has.

Ubuntu has worked with NTFS for years. About 4 years ago it had some reliability issues, so many then were suggesting FAT. Now NTFS on Ubuntu is as good as most file systems. Also with files now often larger than 4GB you have problems with FAT. It will not save a file over 4GB and may not tell you that is only saved part of it. Also for larger partitions you want a journal so it can be repaired easily. 

NTFS does not support Linux file permissions and ownership, so you cannot use it for Ubuntu (except with wubi), just use it for a shared data store for any data you want to use in both windows & Ubuntu.

I converted to 64 bit about 2 years ago and at the same time converted my shared data partition from FAT32 to NTFS. I have had not issues related to using NTFS. I also do not recommend directly writing into the windows system partition, reading is ok, so mount it read-only to avoid accidentally damaging system.

---

### Post by HappyLinux on 2010-12-24
well it's good to know that Ubuntu can handle NTFS read/write.

I have no intention of altering Win7 from within Ubuntu if that's what you mean. Or do you mean installing Ubuntu onto an NTFS partition? If so, then I know that's not possible. It'd be the usual ext4, unless Ubuntu still only uses ext3, plus the separate swap partition. Basically I'll just tell Ubuntu to use the free space on the HDD to create its partitions on its own, and hope that it doesn't try to shrink Win7's NTFS partition.

Basically the computer will come with a 1TB HDD. I intend on using half for each OS; that's practically 500GB for Win7 and 500GB for Ubuntu. Last time I tried to use Ubuntu (I think it was Ubuntu 8.04), it kept trying to shrink WinXPs partition by as much as a third even though it had like 250GB to make use of.

All that's basically on my 2 USB HDDs is the usual things that you find as backups. As I don't use recovery disks, ghosts etc, all that's on the HDDs is straight up photos, audio, vids, documents, downloaded but not installed programs, drivers, that sort of thing.

I agree that NTFS is better than FAT32, but I haven't reformatted the HDDs since I last used Linux so many years ago. So I guess it's going to take me quite some time to transfer the data somewhere else temporarily and so that I can do a reformat of them.

So cheers for the clarification.

---

### Post by oldfred on 2010-12-24
Maverick does not have the install into free space option. It is just better to partition in advance. And having a smaller root partition makes the system more efficient as the drive does not have to search over as large of a space. Same for windows. A bit smaller system partition 50-100GB and larger data partition. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by HappyLinux on 2010-12-27
The computer is coming with 4GB of memory. I don't bother with hibernate or sleep modes. I always turn them off in windows because I'd rather save money instead of wasting energy. No point shutting down the system into sleep or hibernate when I'm going to turn the computer off at the mains socket after shutdown. The only thing that I have on sleep mode is the monitor. I use the sleep mode instead of screen saver graphics. I also turn hard drive sleep off.

I think I see how to setup the dualboot from the guide [http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/~herman546/p22.html")

I just won't try shrinking the Win7 partition where Win7 will be installed on. Come on, Win7 will have almost 500GB, and Linux will have the same to make use of. Plus I'll need the space for Win7 due to gaming, and you know how much space games require now-a-days. Starcraft2 needs something like 12GB, then there's Sim3. You got what 8GB for the starter, then adding like another 3GB per add-on as they come along.

Cheers for that. It'll help when the time comes.

---

