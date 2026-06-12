---
title: "HELP NEEDED on new desktop!!!"
date: 2010-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bugsys on 2010-04-16
Hi all, 

I've been using Ubuntu for a few years now, and find that it is my favorite OS and caters for 80% of my software requirements. Also, the time has come to buy a new desktop.

I have settled that a dell Studio XPS 8100 would be the best choice. However my dilemma lies elsewhere.

My line of work entails that I'll be working with programs which require the 64bit thingy, and the Windows 7 OS. (sorry I don't know much about computers I only know how to use them!!). Namely I'll be working on solidworks, 3ds Max, autocad and Matlab. (ALSO NOTE that these are probably the only programs I'll use in windows).

On the other hand, I dislike windows and I would like to be able to work on ubuntu at the same time. 

Should I leave the pre-installed windows 7 as is and install ubuntu through virtualbox, or the vice versa? 

I understand that the OS running on the virtualbox will be somewhat slower, but the bulk of my time will be spent on ubuntu. 

If I install a 32 bit version of Ubuntu, Will I be able to install a 64 bit version of windows 7 on virtualbox?

I understand that the 64 bit Ubuntu also has some limitations on the software availability... How severe are these limitations, and is there a place where I can found the (main) available software?

Has anyone faced similar dilemmas? 

Any suggestions are welcomed!

---

### Post by Sub101 on 2010-04-16
Which version of the 8100 will you be buying?

If it is either the 6GB or 8GB ram models I would have thought virtualisation would be the way to go.

---

### Post by bugsys on 2010-04-16
Thanx for the very fast reply!

I'm looking at the i5 3.20ghz model, with added ram to 8GB.

Base OS being?

---

### Post by reiki on 2010-04-16
I can tell you how I handled this same type of situation.

I bought my Dell machine with Windows 7 64-bit preinstalled. I let it start for the first time to complete the Windows7 installation. Then I immediately used the disk utility in Windows 7 to shrink the Windows partition. Do this BEFORE INSTALLING ANY SOFTWARE. In your case, you'll want to know how much room will be required by AutoCAD, 3DS Max, MatLab, etc, so you know how small you can make the windows partition.

Once you have the windows partition smaller, you can install Ubuntu to the (now unallocated) free space on the hard drive. 

Why did I choose to do it this way? Because it retains the Dell utility partition and the factory installed OS. I you ever have to call for support, and you tell them you're running Ubuntu, the first thing they'll tell you to do is to restore the system to factory default. Also if there are BIOS updates or whatever, it is much easier to just boot to win7, go to Dell's site and get your updates in a way that the system expects.

I have 8GB of memory. After I installed Ubuntu, I installed Windows 7 into a virtualbox as well. So I can run Windows7 from within Ubuntu, but if I boot to Windows 7 natively, I don't have a virtualbox inside there to run Ubuntu. Simply a matter of choice. You could install Virtualbox into Windows 7 and tehn install Ubuntu in there as well. I just didn't feel the need. I boot to Ubuntu almost exclusively. Some of your programs may run just fine in the Windows virtualbox. I suspect that some might not run as well as you'd like due to their graphics needs. 

So I have Win7 64-bit native, Ubuntu 64-bit native, and tehn Win7 64-bit inside virtualbox on the ubuntu side.

Does that help?

---

### Post by bugsys on 2010-04-16
Thanx reiki, it does help.

My main concern on virtualisation was exactly that solidworks and Max wouldn't run smoothly. 

I guess the dual boot is a necessary evil... 

Cheers man

---

### Post by reiki on 2010-04-16
> **bugsys said:**
> Thanx reiki, it does help.

My main concern on virtualisation was exactly that solidworks and Max wouldn't run smoothly. 

I guess the dual boot is a necessary evil... 

Cheers man

don't forget to do the partition shrink on Windows 7 IMMEDIATELY once it has booted to a desktop for the very first time.

Then it's simple:
Go to Control Panel
Type "partition" into the search box (without the quotes)

that will bring up the disk utility. Basically you want to shrink the largest partition (usually C:) as that's where Windows 7 is installed. You may see one or 2 smaller partitions that may be labeled as "System Reserved". Those are the Dell Utility partition and the restore partition. I remember them as being quite small. I think one of them was only 100MB.

You want to do this immediately because some software writes to sectors well beyond the end of the used areas of the disk and marks them as not movable. If that happens you won't be able to shrink the partition past those immovable sectors.

Some folks would say to just clear ALL partitions and start from scratch. The advantage to doing that is that you get the most usable hard drive space. However, my feeling on it is that I bought a system that includes support. I don't want to negate that support and have to restore to factory fresh if I have a support issue. I ordered my machine with a 750GB hard drive and I have an eSATA external of 640GB. So I can spare a little space.

---

### Post by bugsys on 2010-04-16
Yeah, I totally agree that's why I was thinking about retaining the pre-installed windows 7 and ubuntu on virtual, but it doesn't seem fair for ubuntu to be the one on the virtualbox does it? :P 

A small partition for windows should be adequate, and there should be ample space for everything to work fine!

---

### Post by acepelon on 2010-09-13
> **reiki said:**
> I can tell you how I handled this same type of situation.

I bought my Dell machine with Windows 7 64-bit preinstalled. I let it start for the first time to complete the Windows7 installation. Then I immediately used the disk utility in Windows 7 to shrink the Windows partition. Do this BEFORE INSTALLING ANY SOFTWARE. In your case, you'll want to know how much room will be required by AutoCAD, 3DS Max, MatLab, etc, so you know how small you can make the windows partition.

Once you have the windows partition smaller, you can install Ubuntu to the (now unallocated) free space on the hard drive. 

Why did I choose to do it this way? Because it retains the Dell utility partition and the factory installed OS. I you ever have to call for support, and you tell them you're running Ubuntu, the first thing they'll tell you to do is to restore the system to factory default. Also if there are BIOS updates or whatever, it is much easier to just boot to win7, go to Dell's site and get your updates in a way that the system expects.

I have 8GB of memory. After I installed Ubuntu, I installed Windows 7 into a virtualbox as well. So I can run Windows7 from within Ubuntu, but if I boot to Windows 7 natively, I don't have a virtualbox inside there to run Ubuntu. Simply a matter of choice. You could install Virtualbox into Windows 7 and tehn install Ubuntu in there as well. I just didn't feel the need. I boot to Ubuntu almost exclusively. Some of your programs may run just fine in the Windows virtualbox. I suspect that some might not run as well as you'd like due to their graphics needs. 

So I have Win7 64-bit native, Ubuntu 64-bit native, and tehn Win7 64-bit inside virtualbox on the ubuntu side.

Does that help?
I have a requirement to install a program that only works in 64-bit mode, and I have Ubuntu Lucid 64 bit installed in a partition on my Dell Zino 400.  I loaded up Virtualbox and VMWare both, tried to install the 64 bit guest OS, and it won't install as 64 bit.  I looked in the BIOS and I have Secure Virtual Machine Mode enabled (if it is even required) and I have all of the other parameters in VirtualBox, for example, that need to be checked to make my guest OS 64 bit, but I can't get 64 bit to save my life in those guest OSs.  Do you have any wisdom for me?  Sounds like you have it working.  I had it working at one time, but I blew away my virtualbox images for various reasons and have run into these problems ever since reinstalling new VB and VM images.

Thank you,
Aaron

---

