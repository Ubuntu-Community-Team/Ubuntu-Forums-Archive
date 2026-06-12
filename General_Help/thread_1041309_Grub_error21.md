---
title: "Grub error:21"
date: 2009-01-16
forum: General Help
---

### Post by pkicyris69 on 2009-01-16
Alright guys, I recently (last night) installed ubuntu 8.04 onto a flash drive. It worked perfectly, however, I went to feel if the flash drive was getting to hot. Sometimes my computer likes to fry USB devices. I barely moved it on touch but it dismounted and cause me to restart.

Here is the best part. ERROR: 22 at first, then now its ERROR: 21
I've search everywhere for any solution. I've download Super Grub Loader or whatever it's call but that is just a grub command line which has proved useless since none of what I've read worked.

My BIOS will not recognize my linux HDD. I have 5 hard drives in my system. My linux drive is partitioned on a blank 1TB drive which will not show up to even perform the liveCD install on page one.

Here is what I get from this:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
40 heads, 60 sectors/track, 203498 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf06a9756

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488394581   244197259+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf638f638

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16065  1953520064   976752000    5  Extended
/dev/sdb5           16128  1953520064   976751968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf2dcf2dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       16065   976768064   488376000    5  Extended
/dev/sdc5           16128   976768064   488375968+   7  HPFS/NTFS


Disk /dev/sda: 250.0 GB
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488394581   244197259+   7  HPFS/NTFS

That is my main hard drive containing Windows XP Pro SP3, I can not afford to loose it or any of the data on it same goes for my linux install. I can't even mount it or any other partition from inside Ubuntu 8.04 livecd. I'm not linix savvy, I've been using it for some time but haven't gotten all the ropes. I'm currently taking a linux course in college but I don't/can't wait till thats over to fix my computer.

I'm currently running Ubuntu from a the liveCD. IF anyone could guide me I'd be forever grateful!

---

### Post by pkicyris69 on 2009-01-16
Alright guys, I recently (last night) installed ubuntu 8.04 onto a flash drive. It worked perfectly, however, I went to feel if the flash drive was getting to hot. Sometimes my computer likes to fry USB devices. I barely moved it on touch but it dismounted and cause me to restart. My actually Ubuntu install is 8.10

Here is the best part. ERROR: 22 at first, then now its ERROR: 21
I've search everywhere for any solution. I've download Super Grub Loader or whatever it's call but that is just a grub command line which has proved useless since none of what I've read worked.

My BIOS will not recognize my linux HDD. I have 5 hard drives in my system. My linux drive is partitioned on a blank 1TB drive which will not show up to even perform the liveCD install to replace the grub loader.

Here is what I get from this:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
40 heads, 60 sectors/track, 203498 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf06a9756

Device Boot Start End Blocks Id System
/dev/sda1 * 63 488394581 244197259+ 7 HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf638f638

Device Boot Start End Blocks Id System
/dev/sdb2 * 16065 1953520064 976752000 5 Extended
/dev/sdb5 16128 1953520064 976751968+ 7 HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf2dcf2dc

Device Boot Start End Blocks Id System
/dev/sdc1 * 16065 976768064 488376000 5 Extended
/dev/sdc5 16128 976768064 488375968+ 7 HPFS/NTFS


Disk /dev/sda: 250.0 GB
Device Boot Start End Blocks Id System
/dev/sda1 * 63 488394581 244197259+ 7 HPFS/NTFS

That is my main hard drive containing Windows XP Pro SP3, I can not afford to loose it or any of the data on it same goes for my linux install. I can't even mount it or any other partition from inside Ubuntu 8.04 livecd. I'm not linix savvy, I've been using it for some time but haven't gotten all the ropes. I'm currently taking a linux course in college but I don't/can't wait till thats over to fix my computer.

ask me for any info or cmd needed and the info posted
I'm currently running Ubuntu from a the liveCD. IF anyone could guide me I'd be forever grateful!

---

### Post by cariboo on 2009-01-16
According to your listing, you don't have any linux partitions. Was your Linux partition on /dev/sdb?

All you have there is an extended partition and an NTFS partition. I looks like some how you managed to remove your partitions.

I would suggest booting from the LiveCD and installing testdisk to try and recover your missing partitions. Testdisk is in the repositories.

Jim

---

### Post by caljohnsmith on 2009-01-16
So is your flash drive the 1 GB sdb drive that fdisk shows? If so, it has an NTFS partition which can't be right, and also the partition is logical, not primary. Which tool did you use to install Ubuntu to your flash drive? Did you use UNetBootin, or maybe the USB installer under System > Admin > Create a USB Startup Disk? How about posting the output of the following command:
```
sudo mount /dev/sdb5 /mnt && ls -l /mnt
```

---

### Post by Herman on 2009-01-16
:) **There are two entire hard disks missing!**

Originally posted by pkicyris69
> My BIOS will not recognize my linux HDD. **I have 5 hard drives in my system**. My linux drive is partitioned on a blank 1TB drive which will not show up to even perform the liveCD install to replace the grub loader.**The fdisk output pkicyris69 posted only shows three hard disks, sda, sdb, and sdc.**

Below that, pkicyris69 has posted a copy of the fdisk ouput for sda again, and emphasized how important it is for that hard disk to be preserved.

:-k pkicyris69, how are all these hard drives plugged in to your motherboard? 
I assume some will be IDE hard drives and some will be SATA drives?
Which kind are the two hard drives that are not showing up, (IDE or SATA)?

Maybe you need to check the way your hard drives are plugged in to your motherboard and also check the jumper settings for all your IDE hard drives, and also your CD/DVD drive too.
> Sometimes my computer likes to fry USB devices8-[ Actually, I'm a bit worried about this strange problem you're having with your computer 'Sometimes my computer likes to fry USB devices', I'm worried that it might like to fry hard drives too maybe?
Perhaps you should go into your BIOS right away and go into 'System Health Check' or find something in there like that where you can check what voltages your power supply is putting out, and temperatures and other things like that and make sure your hardware is all okay first, before we try to fix anything in the software.
Here's a link to my BIOS page, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm"), which illustrates what it's like inside the BIOS of one of my computers. 
Yours will be different most likely, but I just wanted to show you what I mean by [System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check"). All BIOSes have something like that, but it might have a different name. Try to find that.

Is your computer located where it can get plenty of cool air, (not too close to a wall), with no plastic or papers blocking any air intake vents? And is it able to freely blow hot air out of the case with the power supply fan and maybe a case fan? Please check your air flow. (I recently fixed a computer and afterwards while testing to make sure it was really alright, I noticed a lizard stuck in the power supply fan! (LOL). Probably there aren't lizards when you live, but just be aware not to overlook the simple things. Overheating is probably the leading cause of failure for most computer parts, especially where I live, where the ambient temperatures can be quite hot as well.

Regards, Herman :)

---

### Post by ajgreeny on 2009-01-16
Are you sure you have 5 hard disks, because only 3 are showing in your ```
sudo fdisk -l
``` output, sda, sdb, and sdc.  I wonder if you are getting mixed up between partitions and disks; windows will call a partition a separate disk, ie C: D: E: etc etc, but they could all be on one physical disk.  I assume also that you issued that command without the USB flash drive attached.  If not and it was attached, there could be a problem with it, though that still does not explain the disk number inconsistency.

Perhaps we have misunderstood and you only have the one ubuntu install which is 8.10 on the flash drive, and no other ubuntu on a hard drive.  Can you enlighten us a bit more please.

---

### Post by pkicyris69 on 2009-01-16
I have 5 physically drives. 2 500gb 2 1TB and one main 250gb. I'm an IT just to give some background info just not a hardcore linux user.
That is all my bios and livecd are posting the hdds mentioned above.

testdisk requires to be installed,

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

The only ones being shown are 
my storage 1tb, my 500gb backup drive which are mounted or visible in the computer section of ubuntu. If I could somehow forcemount my main 250gb drive and back it up then i could just reinstall windows as a last resort.

If there is any other info you guys need or a way to reinstall/repair the grub install on my main hard drive.

I have had 8.04 installed on a separate single drive from windows for about a year I went from 8.04 to 8.10. Then realized i could take linux with me via USB so I used my only live disk i could find which happened to be 8,04 to install it on the flash drive and currently use the livecd to chat here.

---

### Post by Zeroberry on 2009-01-16
Gotta watch out for those computer lizards.

---

### Post by pkicyris69 on 2009-01-16
Well, I managed to be able to force mount my main 250gb windows drive :) Backing it up now, prob take all day moving 200+ gigs from one HDD to another.

Oh, on that note. All my hard drives are SATA.

---

### Post by Herman on 2009-01-16
One of the programs I like is called 'lm-sensors', and you can install it with,
> sudo apt-get install lm-sensorsThe output from a sensors command looks something like this,
```
herman@amd64hh:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +29.0°C                                    
Core1 Temp:  +38.0°C                                    

it8716-isa-0d00
Adapter: ISA adapter
VCore:       +1.01 V  (min =  +0.00 V, max =  +4.08 V)
VDDR:        +4.08 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.18 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +4.84 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +11.46 V  (min =  +0.00 V, max = +16.32 V)
in5:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +6.85 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.09 V
fan1:       3199 RPM  (min =    0 RPM)
fan2:       2177 RPM  (min =    0 RPM)
temp1:       +38.0°C  (low  =  +0.0°C, high = +95.0°C)  sensor = thermal diode
temp2:       +59.0°C  (low  =  +0.0°C, high = +127.0°C)  sensor = transistor
temp3:      +128.0°C  (low  =  +0.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +1.375 V

```
> Well, I managed to be able to force mount my main 250gb windows drive :smile: Backing it up now, prob take all day moving 200+ gigs from one HDD to another.
Oh, on that note. All my hard drives are SATA.
:) Okay, your computer's hardware checked out okay then I presume, good.

 If you're planning on keeping your computer running all day, you might find it interesting to keep an check on your hardware with lm-sensors from time to time, and see that everything's running okay. 
I have icons added on my top panel to display all my sensor info graphically all the time in addition to being able to run the command.
Fluctuations in your power supply voltages would be a bad sign. Power supplies are probably the most common hardware item to cause trouble, and a new power  supply is pretty cheap, especially if you have a standard ATX case and PSU.

---

### Post by Herman on 2009-01-16
hddtemp is the program for monitoring your hard drive temperatures.
```
sudo apt-get install hddtemp
```
For my computer, (with four hard drives), the command looks like this, but you might want to add another one on the end for your fifth hard drive,
```
sudo hddtemp /dev/sda && sudo hddtemp /dev/sdb && sudo hddtemp /dev/sdc && sudo hddtemp /dev/sdd
```
Here's an example of the output you might expect,
```
/dev/sda: WDC WD1600AAJS-00PSA0: 34°C
/dev/sdb: WDC WD1600AAJS-00PSA0: 38°C
/dev/sdc: WDC WD1600JB-00REA0: 27°C
/dev/sdd: WDC WD1600JB-00REA0: 40°C

```If you want them displayed as icon on your top panel, just right-click an empty space on your top panel and click 'Add to Panel', and choose 'Hardware Sensors Monitor'.

---

### Post by Herman on 2009-01-16
> Gotta watch out for those computer lizards.@ Zeroberry, yeah, (LOL), the lizard didn't look very happy about the situation either!

It was a gecko, which is common around the world in tropical countries.
Geckos are very interesting and entertaining creatures, they can not only climb walls, they can easily hang upside down on people's ceilings as well. And if that's not enough, they can actually run upside down across a ceiling fast enough to catch insects! They can change color too, like a chameleon.
I have a colony of them in my house, they're harmless and quite amusing to watch. They play, hunt, and sometimes they fight over territory too.
I'm getting off topic here, but if you have time, check out this interesting Wikipedia link on Geckos, geckos are another example of truth being stranger than fiction, [*Gecko* - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=2&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FGecko&ei=cwVxSa7lDoK2sQOLhoieBA&usg=AFQjCNED_VB3f-q4xMaifVUs5lj_jrlCYg&sig2=X08sLONnWZ6uIzJ7HEhveg")

Regards, Herman :)

EDIT: I forgot to mention that you should also click on some of the links at the bottom of the Wikipedia page, some of those are even more interesting than the Wikipedia page..

---

### Post by bapoumba on 2009-01-16
2 posts from another thread moved in here.

---

