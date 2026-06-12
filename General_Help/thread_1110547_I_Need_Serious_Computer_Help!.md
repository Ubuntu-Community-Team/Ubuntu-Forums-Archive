---
title: "I Need Serious Computer Help!"
date: 2009-03-29
forum: General Help
---

### Post by Spongejerk89 on 2009-03-29
Ok, I have a huge problem. Ubuntu was flipping out and not working so I deleted the Ubuntu partition, but when I restarted Windows it wouldn't start; it just said "Grub error", Anyways, I used my recovery disc like I always do when something goes horribly wrong but it's not working now. So, in order to have a working computer I installed Ubuntu over everything(I'm on it now). Anyway, what should I do? Should I download a new Vista iso, burn it, and install it? I need Windows.


-More Detailed Below-

I just want to install vista back on and that's it. Currently Ubuntu is taking up the whole HDD. After I messed up the partitions there was no working OS on the HDD. I would use the recovery disc, it would do it's thing, and seem to work, but when I restarted it it would just show a grub error, After, that I decided to install Ubuntu over the whole HDD, Vista partition included, so that I would have a working OS. Once Ubuntu was installed and working I decided to restart and put in the recovery disc again, but it doesn't work; the recovery progress just stays are 0%.

---

### Post by protodog on 2009-03-29
Hi,

If you've overwritten your entire disk with Ubuntu, then you'll have no way of recovering Windows. It's gone forever unless you're willing to spend mucho dinero for a computer forensics guy to recover some of what you've lost--even then, it's not sure he can recover anything.

As for the Grub error, it probably means that during your initial Ubuntu installation, you wiped out your Master Boot Record (MBR) which Windows needs in order to boot, and since you couldn't complete your Ubuntu installation, Grub wasn't able to find any operating system to boot to.

My advice is: forget about Windows, you should've backed up your data before installing any OS, and go with Ubuntu. It's a new life and a better one :)

---

### Post by protodog on 2009-03-29
If you absolutely need Windows though. Install Windows over again. Once installed, go into Windows and find out if you have enough space for Ubuntu (~3GB). After that install Ubuntu taking care NOT to wipe out the MBR--essentially you need to set up your system for dual-booting so you can have both Windows and Ubuntu.

---

### Post by linorics on 2009-03-29
Life above, if you used all of your disk space on ubuntu, windows is gone. If you just installed windows over your ubuntu and your getting the black and white screen that says GRUB:> you need to fix you MBR. I use BootIt [http://www.terabyteunlimited.com/downloads/bootitng.zip](http://www.terabyteunlimited.com/downloads/bootitng.zip). Burn it to a CD and just hit cancel until you get something that looks like a desktop. Open you disks and from there you can rebuild your BMR.

---

### Post by HermanAB on 2009-03-30
Install Virtualbox or VMware and install windows XP in a virtual machine.  Dual booting is totally last century...
;)

---

### Post by jaqrah on 2009-03-30
Virtualbox is excellent, I agree.

But until Ubuntu actually has an app that reads my tv tuner card and doesn't take a computer pro to set up (yes I am talking about you MythTV!)or I can access my tv tuner card from inside VBox, I will be dual booting with XP MCE 2005.

---

### Post by Spongejerk89 on 2009-03-30
Ok, I know that my old version of Windows is gone; I just want to install a fresh version. I've tried to use the recovery disc but it just gives me a Grub Error. Also, after I used the recovery disk I use Gpart to look at, and edit my partitions. There I saw a new Vista partition, but when I boot it doesn't show up; just the Grub Error. I've tried deleting all my partitons, using Boot and Nuke to clear my HDD and the recovery discs, but nothing works. I always end up reinstalling Ubuntu 8 again so I can research. I really need Windows, and this is my only computer.  If they had just given me a Vista 64bit installation disc with my laptop than I would be fine!

---

### Post by ispy on 2009-03-30
In that case just install windows over Ubuntu and then use Gparted in the Ubuntu live CD to resize the windows install and reinstall Ubuntu into a dual boot.

---

### Post by Spongejerk89 on 2009-03-30
I've pretty much realized that I need a fresh installation, but they didn't give me an installation disc with my computer. I'm trying to find a good download but it's hard. I'll probably have to buy a new installation disc, download one, or take it to a computer repair shop. Uggggggggh.

---

### Post by Hobgoblin on 2009-03-30
> **Spongejerk89 said:**
> I've tried to use the recovery disc but it just gives me a Grub Error.

Are you sure you are not missing the "press any key to boot from CD" message?

It seems strange that you would still be getting a grub error after using Boot and Nuke.

---

### Post by Spongejerk89 on 2009-03-30
> **Hobgoblin said:**
> Are you sure you are not missing the "press any key to boot from CD" message?

It seems strange that you would still be getting a grub error after using Boot and Nuke.

No, Boot and Nuke won't work; it gives me an error before it does it's "Thing".

---

### Post by Spongejerk89 on 2009-03-31
Ok, the Vista installation disc I'm downloading is taking forever so I'm downloading an XP installation disc. I'll install that so that the Windows boot record is back in tact and than use my computers recovery disc. Does that sound like a good plan?

---

