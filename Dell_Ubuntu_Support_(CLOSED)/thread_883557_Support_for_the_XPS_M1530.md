---
title: "Support for the XPS M1530 ?"
date: 2008-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Carroarmato0 on 2008-08-08
I'm planning to buy the XPS M1530 in Europe. However that model isn't supported with Ubuntu (duh, only in the US).

So checking out Dell's website in the US I saw that they officially supported it, pre-installed with the latest Ubuntu (8.04).

Taking a look at their support page for that model, the only drivers they had available were for Windows Vista.

My conclusion: they support everything out of the box for Ubuntu.

But here's the question: it's shipped with a Ubuntu CD. Is that an official Ubuntu CD, or is it a modified version by DELL?


I contacted a sales representative for Dell America, my conversation with her is attached.

---

### Post by jwalker on 2008-08-08
Uh... I don't know. But I will tell you about my 1530 which I got about two months ago. 

It came with Vista (Dell did not offer Linux here in the UK, which is fine)but Ubuntu went on fairly quickly (like immediatly, I mean). My specs were 2.5Ghz, 4GB, and the highest resolution screen there was, I recommend doing this because this more than anything else will future proof your machine. The laptop itself kicks tail, the speakers however, do not. 

Nor does the 64 bit version of Ubuntu, at least not at this point. Most of the problems that plague other 64 bit users were not apparent. I chucked it out for the 32 bit version after noticing long delays when skipping tunes in Amarok whilst at the same time copying large files. OK I may be a bit demanding but I don't expect my 64 bit power OS to behave like that. 

So I went to 32 bit and life is good again. With Compiz turned off this laptop screams, its very quick. With compiz turned on there's always that 'slight' delay the first time you run anything, click on any menu, I have decided this is a compiz thing and specs don't matter. And 64 bit will always be there, when it gets its act together. 

Ubuntu is sweet with the hardware, everything works, even the webcam, but you need to turn that on. 

But to answer your question, I would wager that the CD Dell ship is whatever Cannonical have hooked them up with.

My advice is get Vista, dual boot with Ubuntu, modify your menu.lst to have Ubuntu boot by default unless you push 'escape' and just the right time when you start. You'll never know you have Vista but its nice to know its there, it occasionally has its uses. *cough Gears of War cough*

---

### Post by Carroarmato0 on 2008-08-08
Thanks for the reply! :KS

---

### Post by jwalker on 2008-08-08
LOL I just read that chat with the Dell lady. It was funny, lots of smiles all around :)
Too bad she was completely useless when dealing with any Ubuntu enquiries.

---

### Post by jwalker on 2008-08-08
Oh and I did just remember that under 64 bit the mouse track pad was fine, but under 32 it didn't work, insane behaviour, this behaviour has been logged by other users and adding some info to your xorg will suss it out. Can't scroll with it though, which suxors.

---

### Post by doojsdad on 2008-08-08
To answer your CD question, for my 1420N at least they shipped with just a general Canonical CD. But, in the past they have released via the web their own ISOs with "issues" fixed.

[http://linux.dell.com/wiki/index.php/Products/Client](http://linux.dell.com/wiki/index.php/Products/Client)

They have done so for 7.04 and 7.10, but not 8.04 yet.

---

### Post by edmccaffrey on 2008-08-10
Any idea if it can support a dual monitor setup with whatever it has plus a 1920x1200 monitor?

---

### Post by jwalker on 2008-08-11
What a specific question. Odd that I tried this myself just the other day when I brought my 1530 into work, where I have a huge muck-off 1920x1200 monitor. The answer is yes, it does support, with a little bit of mucking around in nvidia settings. Stretch the sceen between two monitors or have two sperate desktops.

---

### Post by TimDaniels on 2008-08-16
> **Carroarmato0 said:**
> I'm planning to buy the XPS M1530 in Europe. However that model isn't supported with Ubuntu [....]
But here's the question: it's shipped with a Ubuntu CD. Is that an official Ubuntu CD, or is it a modified version by DELL?

Dell supplies the standard Ubuntu with the appropriate drivers picked out.  Unlike with their 7.10 download, though, Dell's downloadable .iso file for 8.04 does more than set up the Ubuntu partition to the as-delivered state - it **erases the entire disk** before doing that, plus it sets up a utility partition and another recovery partition and the Linux swap partition.  If you intend to add Ubuntu as a dual-boot with a pre-installed Vista, just use the standard Ubuntu downloadable installation file from the Ubuntu website and install it as a dual-boot.  (It wil fit on a CD, as opposed to Dell's 4GB downlod.)  If you intend to use Vista's boot manager as the initial boot manager, put Grub in the Linux partition and adjust Vista's BCD using either Vista's own bcdedit command, or use VistaBootPro or EasyBCD to do it.  If you instead want to use Grub as the initial boot manager, just install Grub to the MBR.  Post again if you need more pointers on setting up the dual-boot scenario.

*TimDaniels*

---

### Post by Carroarmato0 on 2008-08-16
Don't worry about that. I'm planning on using Ubuntu only on it. I'm going to transform the existing Vista partition in a vmx file to keep around in case I need it.

So where can I find this Dell iso file? So in order to install Ubuntu on it even though they don't support it on this machine, will it work entirely out of the box with just the plain Ubuntu cd. Or will I have to install Ubuntu with Dell's cd anyway?

---

### Post by superm1 on 2008-08-16
> **Carroarmato0 said:**
> Don't worry about that. I'm planning on using Ubuntu only on it. I'm going to transform the existing Vista partition in a vmx file to keep around in case I need it.

So where can I find this Dell iso file? So in order to install Ubuntu on it even though they don't support it on this machine, will it work entirely out of the box with just the plain Ubuntu cd. Or will I have to install Ubuntu with Dell's cd anyway?
Ubuntu is supported on the 1530, but if you chose some particular hardware that doesn't normally ship with the Ubuntu option, that may not be supported.

You can either use the ISO from linux.dell.com or you can use the Ubuntu ISO.  The one from linux.dell.com will just preinstall a few of the proprietary bits and add in a recovery framework.

---

### Post by TimDaniels on 2008-08-16
> **Carroarmato0 said:**
> So where can I find this Dell iso file? So in order to install Ubuntu on it even though they don't support it on this machine, will it work entirely out of the box with just the plain Ubuntu cd. Or will I have to install Ubuntu with Dell's cd anyway?

Here is the Dell download site:  [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04).  Since the DVD wiped my entire disk, puting in place a utility partition, a recovery partition (both of which I don't need) in addition to the Ubuntu and swap partitions, I downloaded the generic Ubuntu 8.04 from the Ubuntu website.  That works "out of the box" in my XPS-M1330 with nVidia graphics as far as I need it to (I don't use the webcam, mic, FireWire, highspeed USB or fingerprint reader, so I can't comment on those).  The Broadcom Wi-Fi took several hours of fiddling to get it to work, and I still don't know what finally got it working, but it essentially worked "out of the box".  The driver for my Dell Bluetooth Travel Mouse worked "out of the box", too.  Both the Broadcom and nVidia drivers were "restricted" packages that had to be enabled in the package manager.  In short, as the Dell stated in another thread, there's nothing in the Dell download that the generic Ubuntu installation can't supply, and the generic download fits on a CD (no DVD burner necessary), and it affords you 2 more Primary partitions, and you can partition and set mount points freely.

*TimDaniels*

---

### Post by Carroarmato0 on 2008-08-17
Alright, and does Dell use fixed Primary partitions, or do they install the partitions in a LVM partition?

---

### Post by superm1 on 2008-08-18
> **Carroarmato0 said:**
> Alright, and does Dell use fixed Primary partitions, or do they install the partitions in a LVM partition?
Unfortunately the utility partition must be type de, and the Ubuntu installer doesn't support LVM in ubiquity mode, so primary partitions.

1x type 0xde (utility partition)
1x type 0x0c (recovery partition)
1x type 0x83 (OS partition)
1x type 0x05 (extended partition, swap contained)

---

