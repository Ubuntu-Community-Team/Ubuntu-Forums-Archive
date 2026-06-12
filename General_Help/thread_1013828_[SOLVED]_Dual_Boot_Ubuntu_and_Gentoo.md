---
title: "[SOLVED] Dual Boot Ubuntu and Gentoo"
date: 2008-12-17
forum: General Help
---

### Post by djbushido on 2008-12-17
I was thinking about changing my Xubuntu machine to dual boot both that and Gentoo. I wasn't sure how to partition the drive, boot record stuff, and all of that. 
NOTE: My hard drive is connected externally via USB. I don't know if this is a problem, but thought it should be known.

Any help would be appreciated, i just don't want to do anything stupid and mess up both systems.

Also also: Is there a text only version of the live cd? I would like all the packages, but for some reason my computer doesn't like live cd's, but does okay text only.

Thank you!

---

### Post by Sam Lars on 2008-12-17
As far as the text-based, you should try the Alternate install CD from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors").  It's just the install, not a liveCD though.  Could you boot to the regular CD and then switch to a terminal?

---

### Post by caljohnsmith on 2008-12-17
One of the important points to consider in order to make your desired setup work is to make sure you specify where the boot loaders get installed for Xubuntu and Gentoo. For instance, when you go through the Xubuntu installer, there should be an "advanced" button near the end of the installation (I'm assuming it's similar to Ubuntu's installer) where you can specify where Grub gets installed to. If you can set your BIOS to boot the USB drive, then I would recommend installing Grub to the MBR (Master Boot Record) of the USB drive so that it will be bootable. You can do that by setting the install location as "/dev/sdb" (or whichever is your USB drive) under the advanced settings button. When you go to install Gentoo, I would recommend having Gentoo install its boot loader to the boot sector of its own partition, for example /dev/sdb3 if that's the Gentoo partition, so that Xubuntu stays in charge of the booting process on start up. Then to boot Gentoo from your Xubuntu Grub menu, you can use an entry in Grub's /boot/grub/menu.lst like:
```
title Gentoo
root (hdX,Y)
chainloader +1

```
And replace (hdX,Y) with the correct Gentoo partition. Anyway, that's the basic idea, but let me know if you need more specifics or run into problems. :)

---

### Post by djbushido on 2008-12-17
Okay, to clarify: I have a currently working Xubuntu 8.10 installation.
I am trying to install a Gentoo workstation, and set this up as a dual boot. If you can provide any info on partitioning to allow for Gentoo, that would be appreciated. Otherwise, just let me know that you can't, and I'll post this to a Gentoo forum, or something like that. Thank you again for your help.

Also, as to the existing mbr, it is on the usb device already, not on the main drive, so it is currently booting entirely from the usb device.

---

### Post by Sam Lars on 2008-12-17
If you boot to a liveCD, you can use a partition editor to make a free partition to install Gentoo on.

---

### Post by djbushido on 2008-12-17
Okay, that's partitioning out of the way. How do I configure GRUB?

---

### Post by Sam Lars on 2008-12-17
I think that's where caljohnsmith's info comes in.

---

### Post by djbushido on 2008-12-17
Oh, thanks, didn't read that too in depth. Can't try now, but will post results later. Thank you so much!!!!

---

### Post by djbushido on 2008-12-18
Question on partitioning:
I was going to use this scheme (in order):

ext3 (Xubuntu)
swap? (~2 gb, leaving for whatever)
ext3 (Gentoo /boot)
ext3 (Gentoo root [/])

Is this legal? And should it work? The Gentoo guide suggested having a seperate /boot partition, so I incorporated that, but still can only have 4 partitions. If you guys could let me know if this will work, I would appreciate it. Not planning to do anything else until I hear back. Thanks!

EDIT: Where does swap need to go? End of disk? I will be using a gparted live usb, so I should be able to work with that.

---

### Post by Sam Lars on 2008-12-18
That looks like it should work.  Having a separate /home partition would be ideal, but given your situation, I think what you have there will work fine.

---

### Post by djbushido on 2008-12-18
Yeah, wanted a /home, but I am probably going to be the only one using it so it is not really needed that bad. So, is that setup ok, or do I need to move swap space to end of disk?

---

### Post by Sam Lars on 2008-12-18
As far as I know the location of the swap shouldn't matter, but if you want to do that, it wouldn't hurt.

---

### Post by djbushido on 2008-12-18
Okay, will do partition shrinking and creation, and will get back to you guys soon.

---

### Post by djbushido on 2008-12-18
Okay, this is a bit weird, so hold on.
What happened was i booted a Gparted live usb.
Turns out that it was really slow, so i disable the ehci_hcd mod (usb 1)
Problem: live usb was mounted using that.
So, screwed up resize, and couldn't get it to boot.
Good News: I can still read the drive to get the contents off.

So, what I am going to do now is to make a backup of the drive, first. Then, I will install Gentoo via virtual machine. Then I will install Xubuntu on top of that, which should take care of all of the weird partitioning, just resize and good to go. If you guys have anything against this, PLEASE let me know. Thank you again for your continued support.

---

### Post by djbushido on 2008-12-19
Next question: If I install a package on the live cd (bcm43xx-fwcutter), for both the gentoo and xubuntu installs, will that automatically place it there after the install? Unless I hear otherwise, I will assume it does, but please tell me one way or another.

---

### Post by logos34 on 2008-12-19
> **djbushido said:**
> Okay, this is a bit weird, so hold on.
What happened was i booted a Gparted live usb.
Turns out that it was really slow, so i disable the ehci_hcd mod (usb 1)
Problem: live usb was mounted using that.
So, screwed up resize, and couldn't get it to boot.
Good News: I can still read the drive to get the contents off.

So, what I am going to do now is to make a backup of the drive, first. Then, I will install Gentoo via virtual machine.

if you haven't already gone ahead with the VM option, at least run a filesystem check on xubuntu root from the live cd:

sudo fsck /dev/sdb1

or whatever / is.  Might help, never know

Also, personally I'd [ditch the separate /boot]("http://blog.flameeyes.eu/2007/11/02/why-people-insist-on-using-boot")--for the average desktop it's unnecessary and a waste of a partition

---

### Post by djbushido on 2008-12-20
Okay, ditching /boot.
Also, after 4 hours of fsck running and cloning multiply referenced blocks (or something like that) I gave up and am doing a VM install.

---

### Post by djbushido on 2008-12-21
Okay, now then.
After repartitioning, hours upon hours of compiling Gentoo, hours setting up Xubuntu, I finally have a dual-boot. I am having specific problems with Gentoo, but not wanting to post those here (UBUNTU forums?).
Thank you for all your guys' help, appreciate it a lot.

---

