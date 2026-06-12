---
title: "Problems after install x3"
date: 2009-05-07
forum: General Help
---

### Post by RobCh on 2009-05-07
Hey, I'm a beginner and just did a new install of the latest Ubuntu off the web on my brand new laptop.  I did it side by side of the packaged vista OS.  I'm having several problems and any assistance would be greatly appreciated (please use small words and type slowly ;P)

1. During the installation I wasn't prompted which disk to install to (I have 2x 500Gb).  I also didn't get prompted for a partition size when I got to do the recommended updates it says I have no room on '/'.

2. I'm getting a permanent loop of sound the moment I get into ubuntu and I don't know how to correct this.

3. When I restart from either OS rather than shutdown I get a Grub error and have to manually shutdown and then restart.

kind regards,
Rob

---

### Post by pastalavista on 2009-05-07
Hmmm doesn't sound good. Run Ubuntu from the live cd, open a terminal (Applications > Accessories > Terminal) type ```
sudo fdisk -l
``` and post the output here.

---

### Post by chellrose on 2009-05-07
> **RobCh said:**
> Hey, I'm a beginner and just did a new install of the latest Ubuntu off the web on my brand new laptop.  I did it side by side of the packaged vista OS.  I'm having several problems and any assistance would be greatly appreciated (please use small words and type slowly ;P)

1. During the installation I wasn't prompted which disk to install to (I have 2x 500Gb).  I also didn't get prompted for a partition size when I got to do the recommended updates it says I have no room on '/'.

2. I'm getting a permanent loop of sound the moment I get into ubuntu and I don't know how to correct this.

3. When I restart from either OS rather than shutdown I get a Grub error and have to manually shutdown and then restart.

kind regards,
Rob

I'm not sure if I can be helpful here, but I'll give it a shot...

If I'm reading correctly, you have 2 separate hard drives, right?  That's odd that it didn't prompt you for which disk to use.

What grub error are you getting exactly?

And, finally, can you actually access/log in to Ubuntu?

Edit: oops, too slow!  You should follow pastalavista's advice first, as s/he likely knows far more than I do about this. :)

Good luck.

---

### Post by RobCh on 2009-05-07
pasta here is the output u requested:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa83626ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59265   476043232+   7  HPFS/NTFS
/dev/sda2           59265       60801    12340224    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa133206c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60149   483146811    7  HPFS/NTFS
/dev/sdb2           60150       60801     5237190    5  Extended
/dev/sdb5           60476       60779     2441848+  83  Linux
/dev/sdb6           60780       60801      176683+  82  Linux swap / Solaris
/dev/sdb7           60150       60453     2441817   83  Linux
/dev/sdb8           60454       60475      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order


Note: I still have the sound issue booting from the disk and 'trying ubuntu'

---

### Post by RobCh on 2009-05-07
sissy,

thanks for your reply.  I have a new HP notebook. 2x 500gb HDD.

I can load ubuntu np's.  I just have to mute my sound and everything seems to run ok.  But I can't do the updates because it says I have no space available on '/'

I believe the error is 13 from memory.

---

### Post by pastalavista on 2009-05-07
Well, it looks like you installed Ubuntu twice. The sound problem from the live CD boot tells me you may have burnt a bad copy. It also seems that the NTFS partition on that drive (sdb1) is taking up most of the space. Next time, before you boot the live CD, first run the check disk (don't remember the actual name but it's something like that) in the options below the start-up list. If it checks bad, you'll probably have to download it again, or you might try burning the iso you already have again at a slower speed. Once you have a good burn, run it in the live mode (try without installing) and go to the Partition Editor in System > Administration menu. Then delete the extended partition you installed the ext3 and swap partitions on sdb2. Then resize/shrink the NTFS partition (sdb1) to make a little more room for Ubuntu. Then you can install it again in the empty space. Use the manual mode of the partitioner/installer.That's why you didn't see all your mount options. With two 500 gig drives, that must be one heck of a laptop. I'm jealous.

---

### Post by pastalavista on 2009-05-07
PS.. just a tip. When you install, create a swap partition of about a gig or two, and / (root partition... gotta have that) and if you make a /home partition, large enough to hold all your data, the next time you install/reinstall/upgrade, your settings and personal data will be retained intact and you'll only have to format to the / partition. Good luck !

---

### Post by RobCh on 2009-05-07
> **pastalavista said:**
> Well, it looks like you installed Ubuntu twice. The sound problem from the live CD boot tells me you may have burnt a bad copy. It also seems that the NTFS partition on that drive (sdb1) is taking up most of the space. Next time, before you boot the live CD, first run the check disk (don't remember the actual name but it's something like that) in the options below the start-up list. If it checks bad, you'll probably have to download it again, or you might try burning the iso you already have again at a slower speed. Once you have a good burn, run it in the live mode (try without installing) and go to the Partition Editor in System > Administration menu. Then delete the extended partition you installed the ext3 and swap partitions on sdb2. Then resize/shrink the NTFS partition (sdb1) to make a little more room for Ubuntu. Then you can then install it again in the empty space. Use the manual mode of the partitioner/installer.That's why you didn't see all your mount options. With two 500 gig drives, that must be one heck of a laptop. I'm jealous.

It is a nice laptop, it's a pity I don't have the knowledge to use it at it's full potential :P

That's really incredible u were able to figure that out.  I did have a bad disk and it caused a problem during an install.  I terfed it and made a new disc that works fine.  I redid the install and that's where I'm at.  I don't think it's a bad disk I have now, it verifies fine.  I'm currently running it now while I try to sort this mess out.

In the partition editor it shows:

/dev/sda1 - ntfs - OS - 453.99 GiB - 222.22 GiB (used) - 231.77 (unused) - boot
/dev/sda2 - ntfs - RECOVERY - 11.77 GiB - 9.86 - 1.91

then I go to sdb

/dev/sdb1 - ntfs - DATA .......
then there are the 2 installs of ubuntu sdb7 and sdb5.  I can't delete either.  It asks me to unmount partitions higher than 7 and 5 respectively.  But further playing allowed me to delete the linux-swap (sdb8) and therefor 7.  But I don't know why it suddenly let me and I still can't get rid of 6 so I can then do 5.  Wait..I figured it out...I went to the option 'swap off'.  And now I've deleted sdb2 and now have 221.55Gib unallocated space I can reinstall ubuntu on.  Thanks pasta :)  That was scary.  Atleast it's a new computer and I have nothing to lose really :P

Guess I'll go do that now...but what is the best format to use?  I saw that there is ext4...but the default is ext3 correct?  I expect I'll still have the sound issue tho.

---

### Post by pastalavista on 2009-05-07
I installed in place to the / drive, like I explained in my tip and formatted it to ext4 but left the rest as ext3 because I didn't want to take a chance on losing my data. It boots much faster than 8.10 and seems pretty stable.

Still have the sound issue? running the live CD? Well after you install, it will do about a jillion updates, so maybe it'll have a driver that will fix it. Just wondering what your sound card is. Fancy laptop like that, probably 5.1 surround or maybe even 7.1. You can find out in terminal with:```
lspci -v | grep "Audio"
```
Glad to be of help.

---

### Post by b@sh_n3rd on 2009-05-07
If I may say something here...EXT4 is quite cool but apparently there seem to be some bugs though I haven't noticed and are less likely to occur in Jaunty..that is, Ubuntu 9.04. Anyway, I installed my version of Jaunty with /boot, /root and /home with the XFS filesystem. There is supposed to be a prob with XFS and GRUB but it didn't effect me and that is how im typing this here post :D. Anyway, technically XFS shows a tie in boot time with EXT4 and is faster than EXT4 in disk throughput. In other words, it's the best and fastest filesystem so far, though some dunno about it. I'm glad I did research on it the last time I did a clean install of Jaunty :D. My 11yr old comp boots in 31.10S with a slow HDD. Faster than Winblows anyway...all this reliable thing needs is a good OS like Ubuntu :D.

---

### Post by RobCh on 2009-05-07
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

That came up when I type ur command in terminal.  Hope it means something to you :)  All I know is a got a cute little subwoofer in the bottom :P

So I'm waiting for it to format atm.  I took your advice pasta and made a 2.5G swap partition, a ext 4 / @30G, and the rest is ext3 /home (~200G)

Sound ok?

One day I'll learn how to make it all work best for me.  I'm currently waiting for it to format.

B@sh - think I'll just keep it simple for now lol...I'm still very vague on all this partition and file system stuff.

---

### Post by pastalavista on 2009-05-07
Uh-oh.. I searched your card on Google and found [this]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/274424"). So you'll be having the same problem until the bug is squashed. At least we know the problem is being worked on. Your partition setup looks perfect to me. I wish I had a sub-woofer :( or any kind of woofer for that matter.

Cheers

---

### Post by b@sh_n3rd on 2009-05-07
Hi, well that's okay...EXT4 is good too. It's fast as XFS but for some reason is slower at average disk throughput. Actually, you wouldn't really notice anything whichever filesystem you use. Just the speed at which your system would read your drive which relates to how fast you can manage your files and folders and also how fast your system boots. I recommend XFS, EX4 then EXT3. Even though the ratings cite EXT4 last :D. This website shows the benchmark where I got to know all this stuff about these filesystems, especially XFS. [http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/](http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/)

---

### Post by RobCh on 2009-05-07
OK so I'm all updated now and still have the sound issue.  I looked up the link pasta supplied with the bug relating to my sound card and ppl were posting a solution to get the sound working again.  I can't do that because it says I don't have permission to edit the file...???

I also still get the Grub Error 25 when I restart rather than boot up after a shut down.

Any ideas?

Nevermind...I found how to edit it (use sudo in terminal) :)

Now just the restarting error to go...for now >.<

---

### Post by pastalavista on 2009-05-07
Hey Rob, I'm on my lunch break now and thought I'd check in. Glad to see you're getting up to speed. I've learned that before asking questions, it's best to search this forum with Google like this (site:ubuntuforums.com <inquiry keywords here - no brackets>) or just use the search at the top of the page (Google search is better). I'm not an expert by any means. Only been using Linux myself since my join date. I've pretty much taught myself all I know about Ubuntu doing it that way.[ Here's what I found out]("http://ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25") about your grub error. The thing I like most about Linux is that you can fix problems yourself and don't have to download special software to do it. You're on your way, my man.

Ben

---

