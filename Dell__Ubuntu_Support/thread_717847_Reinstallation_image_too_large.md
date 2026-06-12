---
title: "Reinstallation image too large?"
date: 2008-03-07
forum: Dell  Ubuntu Support
---

### Post by sumguy231 on 2008-03-07
I just got a brand new Inspiron 1420N, and I've had a generally positive experience with it. However, when I wanted to burn the reinstallation iso on the desktop to a DVD, I noticed it is apparently 5.0 GB and won't fit on a DVD. Has anyone else noticed this? Am I overlooking something?

---

### Post by gbrainin on 2008-03-08
I have no idea what the difference between them is (it might be the DVD playback?) but there is an .iso image on the Dell website that will fit on a DVD: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")  There are slightly different versions depending on your model and video card.

---

### Post by sumguy231 on 2008-03-08
Interesting. Still, apparently there's a bootable recovery partition on the hard drive that does the same thing anyway so I don't suppose I'll bother making a disc.

---

### Post by dmery-segp on 2008-03-13
Hi
I have a Dell Inspiron 1420N and I burned the reinstall 7.10 DVD...
Do you know how reinstall dvd is working ? How is the way ? Because when the disc is booting you can chose two options: reinstall o livedvd. I assume that reinstall is the good way...but ....When I reinstall the system all my programs and configuration still remain on my system? Reinstall option is like an update ?
thanks for your help
regards,
dmery

---

### Post by sumguy231 on 2008-03-13
I have no idea, I haven't had a need to reinstall yet. I imagine the reinstall DVD probably does a standard OEM install which would wipe it to factory defaults. You should back up everything in your home directory (including hidden stuff starting with a . ) first before you do that.

---

### Post by RedRat on 2008-03-13
OK, the Dell iso on your desktop is an exact image of your Ubuntu installation so it contains everything you may or may not have added. The more you use the machine, I think it gets bigger. If you want the original Ubuntu image that Dell used for your machine you will have to go to their Web site and download it, it is a bit over 4 GB and will fit on a DVD. Go here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO)

---

### Post by sumguy231 on 2008-03-14
> **RedRat said:**
> OK, the Dell iso on your desktop is an exact image of your Ubuntu installation so it contains everything you may or may not have added. The more you use the machine, I think it gets bigger. If you want the original Ubuntu image that Dell used for your machine you will have to go to their Web site and download it, it is a bit over 4 GB and will fit on a DVD. Go here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO)

I don't think that's true, because I've installed all kinds of things and used a lot more disk space since I made that post and it's still exactly 5.0 GB. Anyway, it's not a big deal just a little weird.

---

### Post by RedRat on 2008-03-14
Well I used my Dell for about a month and then screwed it up by downloading and installing Ubuntu Studio, which caused all kindsof problems with Xserver. When I looked at the iso file on the desktop it was about 6 Gb, the original was about 4.7 Gb. So I suspect that it was really creating an image of the system, that is its actual intent. I believe that it is nothing more than a pointer to a hidden Dell partition, at least I have seen others mention that.

---

### Post by niteshifter on 2008-03-15
I also think it's not correct that the iso "grows". I bought a 1420n late last December. From my installation notes then: (output from ls -al /home, excess info removed for clarity)

-rw-r--r--  1 root root 5328908288 2007-12-26 05:35 ubuntu-dell-reinstall.iso

and just now (and having added many, many MB of software:
-rw-r--r--  1 root root 5328908288 2007-12-26 05:35 ubuntu-dell-reinstall.iso

Nor is it a pointer to /dev/sda2. It is a file. But let us not depend on the mentions of others ;) here's what Dell says on the subject:

> On factory-installed systems, the Ubuntu 7.10 operating system can be re-installed via 2 different methods:

    * From hard drive (recommended): By using the GRUB menu at boot time.
    * From DVD disc: By using the DVD iso provided on your system's Desktop.

Reference URL: 
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation")

---

### Post by mips on 2008-03-15
> **sumguy231 said:**
> I just got a brand new Inspiron 1420N, and I've had a generally positive experience with it. However, when I wanted to burn the reinstallation iso on the desktop to a DVD, I noticed it is apparently 5.0 GB and won't fit on a DVD. Has anyone else noticed this? Am I overlooking something?

Yes you are.

From the Dell website I gather that the Inspiron 1420N (with Ubuntu) by default ships with **OPTICAL DRIVE:  8X CD/DVD Burner (DVD+/-RW) with [COLOR="Red"]double-layer DVD+R write capability[/COLOR]**.

Now the above tells me I should go to a shop and purchace a few 8X DVD+R DL 8.55GB discs. (DL = Dual Layer)

Put the 8.55GB DL DVD+R in your drive and burn the image to disc.

See, easy as pie ;)

---

### Post by sumguy231 on 2008-03-15
Oh yeah, I suppose that would work. Thanks for the reminder. Of course, it's not worth the price of dual-layer discs if they cost as much as they did last time I checked in on them. I'll just use the hard drive restore partition if I ever need such a thing.

---

### Post by RedRat on 2008-03-15
> **niteshifter said:**
> I also think it's not correct that the iso "grows". I bought a 1420n late last December. From my installation notes then: (output from ls -al /home, excess info removed for clarity)

-rw-r--r--  1 root root 5328908288 2007-12-26 05:35 ubuntu-dell-reinstall.iso

and just now (and having added many, many MB of software:
-rw-r--r--  1 root root 5328908288 2007-12-26 05:35 ubuntu-dell-reinstall.iso

Nor is it a pointer to /dev/sda2. It is a file. But let us not depend on the mentions of others ;) here's what Dell says on the subject:



Reference URL: 
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation")

Ok during the meltdown of my system when I attempted an install of Ubuntu Studio, I did exactly that: I attempted to re-install the OS from the desktop iso and when the machine re-booted up came the Ubuntu Studio splash screen and my Xserver would not start. So I figured that the desktop iso had incorporated all of the changes I had made to the system. 

That is why I wiped my disk (there was no great loss of anything important anyway) and re-installed Ubuntu from the Ubuntu disk that Dell ships with the machine. It is just basically the vanilla Ubuntu, not the Dell version. So far it works great on my machine, but probably will go and re-install the Dell version that I downloaded from their site for my particular machine (4 Gb in size and burnable to a standard DVD). 

Nevertheless I have heard via the newsgroups that Dell has some kind of hidden partition. However, I also know that the newsgroups seem to traffic highly in gossip and mis-information also, so I tend to take what I see there with a grain of salt.

---

### Post by jdelaros1 on 2008-03-15
Here is a breakdown of the partitions on Dell-installed systems:

- Partition 1 is for Dell Utilites and Hardware diagnostics,
- Partition 2 is re-install partition, which contains the Ubuntu DVD iso plus scripts and custom debs added by Dell.
- Partition 3 is swap
- Partition 4 is extended partition
- Partition 5 is / 

Reference:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Default_Partitions](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Default_Partitions)

When you re-install from the hard drive (via the GRUB menu) is uses the iso in Partition2. When you burn the iso on your Dekstop, you use the iso in /home. So yes, there are 2 copies of the custom DVD iso on your system. If you want to free up space, burn the iso in /home to a disc and then delete it.

By the way, both isos are static, and they never grow in size. Not sure why people report that it grows in size.

All your personal files are *not* added to either iso, so if you re-install the OS from these isos, be sure to backup everything, as warned on the Dell Wiki.

---

### Post by ShellyLewis on 2008-05-15
> **sumguy231 said:**
> Interesting. Still, apparently there's a bootable recovery partition on the hard drive that does the same thing anyway so I don't suppose I'll bother making a disc.

How did you access it?  Please share.  I am trying to reinstall the original version because I upgraded and am unhappy with my upgrade.

Thanks a million!

---

### Post by ShellyLewis on 2008-05-16
Problem solved.  I found it.  All is well now.

---

### Post by RedRat on 2008-05-16
> **jdelaros1 said:**
> Here is a breakdown of the partitions on Dell-installed systems:

- Partition 1 is for Dell Utilites and Hardware diagnostics,
- Partition 2 is re-install partition, which contains the Ubuntu DVD iso plus scripts and custom debs added by Dell.
- Partition 3 is swap
- Partition 4 is extended partition
- Partition 5 is / 

Reference:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Default_Partitions](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Default_Partitions)

When you re-install from the hard drive (via the GRUB menu) is uses the iso in Partition2. When you burn the iso on your Dekstop, you use the iso in /home. So yes, there are 2 copies of the custom DVD iso on your system. If you want to free up space, burn the iso in /home to a disc and then delete it.

By the way, both isos are static, and they never grow in size. Not sure why people report that it grows in size.

All your personal files are *not* added to either iso, so if you re-install the OS from these isos, be sure to backup everything, as warned on the Dell Wiki.

I am assuming that when I installed the vanilla Ubuntu 7.10 from the Ubuntu Disk, I wiped all those partitions out. Am I correct? How would I find out if there are other partitions?

---

