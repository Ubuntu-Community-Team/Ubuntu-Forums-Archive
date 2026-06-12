---
title: "Has anyone managed dual boot with dm-crypt-Ubuntu and Truecrypt-Windows?"
date: 2009-02-21
forum: General Help
---

### Post by LodeRunner on 2009-02-21
Recent versions of Truecrypt allow you to encrypt the entire drive that Windows is on (this does not currently work with any other OS.)  This is accomplished through the use of a special Truecrypt bootloader.  In theory, it can coexist with Grub but I haven't been able to pull it off yet (Grub keeps disappearing.) 

I have two hard drives; plan is to have Ubuntu with full disk encryption (dm-crypt) on one and Windows with full disk encryption (Truecrypt) on the other. Has anyone managed to pull off this setup yet? If so, how?

---

### Post by legalizemeth on 2009-03-14
I'd be very interested in people's experiences with this as well.

---

### Post by mrsteveman1 on 2009-03-14
You install grub to a /boot partition instead of the front of the disk, and let truecrypt do whatever it wants :) They can coexist like that, i've done it before.

---

### Post by tnt2000 on 2009-03-20
mrsteveman1 could you write a txt-tutorial how to proceed?

---

### Post by mrsteveman1 on 2009-03-20
I will indeed write it up right now :)

---

### Post by street spirit on 2009-03-21
You may also be interested in the threads [here]("http://forums.truecrypt.org/viewtopic.php?t=15301") and [here]("http://ubuntuforums.org/showthread.php?p=6928952") about setting up a an encrypted dual boot system, with the additional requirement of a hidden Windows OS.

---

### Post by mrsteveman1 on 2009-03-21
I have it written up and am taking screenshots right now. The trick is to do the encryption setup manually in the installer and tell grub to install to the /boot partition. 

Will post what i have soon since screenshots were not behaving earlier :)

---

### Post by mrsteveman1 on 2009-03-21
I've gone back and forth between 2 versions of this tutorial, one that uses encrypted LVM like it should, and one that just has a root partition directly encrypted. Lets just say the Alternate install CD installer (which came from debian) just annoyed me for a few hours so i went with the simple route for now.

Here is the simpler version that does not support encrypted swap or hibernation. A normal swap partition could be easily added if you know what you are doing, or you could just put a swapfile on the already encrypted root. Hibernation may or may not work in that case, I'm not entirely sure it works with the normal encrypted setup anyway. It wouldn't take much to add a second encrypted partition for swap which might make hibernation work.

Note that this is simply a single drive install, however if you want to install Ubuntu to the second drive it will work, just make sure grub goes in the right place. Your layout at that point would be one drive with just windows, and the second drive with a /boot partition and an encrypted root partition. As long as you install Truecrypt last it should work.

[http://tech.xerces.com/dual-boot-encryption.geek]("http://tech.xerces.com/dual-boot-encryption.geek")

---

### Post by street spirit on 2009-03-22
> **mrsteveman1 said:**
> Lets just say the Alternate install CD installer (which came from debian) just annoyed me for a few hours so i went with the simple route for now.

Which version did you install? My test installation with the Kubuntu 8.10 alternate disk went well, except that I forgot to tell the installer not to overwrite the MBR with grub. I had to fix that mistake later with the TrueCrypt rescue disk, and by re-installing grub on the correct partition. To be honest, I only installed this multi-boot setup in a VirtualBox VM, but I'm quite sure it will work well enough on my laptop.

[This article by Martti Kuparinen]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html") was a great help for me; it walked me through all the requiredf steps to create an encrypted block device and create logical volumes on it. The only unencrypted partition on the whole laptop is now Linux's /boot, which will never contain sensitive data.

> **mrsteveman1 said:**
> As long as you install Truecrypt last it should work.

I installed TrueCrypt first and chose the multi-boot setup. Since both grub and the TrueCrypt boot loader are capable of handling multiple operating systems, I think either way is fine.

---

### Post by mrsteveman1 on 2009-03-22
> **street spirit said:**
> Which version did you install? My test installation with the Kubuntu 8.10 alternate disk went well, except that I forgot to tell the installer not to overwrite the MBR with grub. 

I used 8.04.2 alternate CD, the main Gnome based one.

> [This article by Martti Kuparinen]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html") was a great help for me; it walked me through all the requiredf steps to create an encrypted block device and create logical volumes on it.

Yes i read that page, it makes no mention of installing the bootloader. When i tried to do the LVM setup manually, it forced me to install LILO and gave no option for grub, then the LILO install failed. I was quite angry, and I hate LILO :)


> I installed TrueCrypt first and chose the multi-boot setup. Since both grub and the TrueCrypt boot loader are capable of handling multiple operating systems, I think either way is fine.

Correct me if i am wrong, but i don't believe the truecrypt bootloader sits in the VBR for the Windows partition, it seems to install its own MBR code and load itself directly instead of doing the standard bios call to bootstrap from a partitions VBR code. But by all means if either way works, good :)

GRUB though i know can be well behaved and sit in the VBR for the /boot partition, so i chose to do that and allow the truecrypt bootloader to chainload it when booting Ubuntu.

---

### Post by street spirit on 2009-03-22
> **mrsteveman1 said:**
> Yes i read that page, it makes no mention of installing the bootloader. When i tried to do the LVM setup manually, it forced me to install LILO and gave no option for grub, then the LILO install failed. I was quite angry, and I hate LILO :)

Hehe, I loathe LILO too, but fortunately it never came to that. The installer just put grub on the MBR (overwriting the TC loader). I then booted Linux and installed grub on /dev/sda3 (which is /boot in my case) and after another reboot used the TC rescue disk to restore the TC boot loader to the MBR. Works exactly as intended: When you boot the machine, TC asks you for a password (for either the decoy or the hidden Windows OS), and gives you an option to hit ESC, in which case it will move on to the grub boot screen.

There's apparently a way to put grub in the MBR and have the TC boot loader chain-loaded. That sounds like the cleanest solution, but the explanation went a bit over my head :-). Anyway, it seems there's more than one way to do it, which pleases an old Perl afficionado like me.

One final gotcha: something (probably the Ubuntu alternate installer) removed the 'bootable' flag from /dev/sda1. If you get weird results like TC reading the password for Windows and then sending you to the grub screen, that might be the problem.

Anyway, it works, which is the main thing. I had a major scare when I lost my laptop for a few hours last week (I thought it was stolen), and after that I realized that full disk encryption is the only way to go, even if it's a bit tricky to set up.

---

### Post by LodeRunner on 2009-05-11
Re: swap

In the age of multiple-gigabyte ram, hard disk caches are rather silly. (In particular, the old "two times your physical ram" rule of thumb is crazy overkill.) For performance and security reasons, I highly recommend compcache.  It sets up a compressed ramdisk to use as a swap partition.  It makes better use of your ram (due to the compression), and it runs MUCH faster than a hard drive (or even flash memory) swap. As an added bonus, you don't have to worry about encryption.

It's very simple to set up:

sudo gedit /etc/initramfs-tools/initramfs.conf 
[change the compcache line to "25%" or some other value.  This is how much ram it uses.]

sudo update-initramfs -k all -c

then reboot. Verify that it's working by going to system=>administration=>system monitor.

> **mrsteveman1 said:**
> Note that this is simply a single drive install, however if you want to install Ubuntu to the second drive it will work, just make sure grub goes in the right place. Your layout at that point would be one drive with just windows, and the second drive with a /boot partition and an encrypted root partition. As long as you install Truecrypt last it should work.

When I tried this a few months ago, I *did* use a /boot partition and I let TC do its thing last, but I think I may have messed up by not having the correct partitions marked bootable (specifically, I think I installed windows second and used some trickery to keep it from overwriting grub.)  I'll give it a shot again right now.

---

### Post by street spirit on 2009-05-11
> **LodeRunner said:**
> Re: swap

In the age of multiple-gigabyte ram, hard disk caches are rather silly. (In particular, the old "two times your physical ram" rule of thumb is crazy overkill.) For performance and security reasons, I highly recommend compcache.

Just for the record, even with multiple GB of RAM, swap partitions do have their place. For example, when you're running a database like PostgreSQL, it's recommended to set the kernel's overcommit_memory to 2 to avoid data loss. In this case, it's a lot easier to run out of memory, and you'll probably see increased swap usage if you ride the limits too closely. Using part of your main memory for swap won't be a solution here. HDD space is cheap (compared to RAM), and it's better to be safe than sorry.

I agree about the 2xRAM rule being outdated. The swap size and settings should reflect the actual usage.

---

### Post by LodeRunner on 2009-05-11
Well, I should have included the disclaimer "on typical desktops / laptops" (which obviously does *not* include large PostgreS databases.)  Servers have their own set of security issues due to the fact that they're always on.  Using compcache on a server is not significantly more secure than using an encrypted OR unencrypted hard drive swap due to the [cold boot attack]("http://en.wikipedia.org/wiki/Cold_boot_attack"). Also, servers are much less likely to have a dual boot setup such as this.

On the other hand, IMO compcache for typical desktop usage is a no brainer, *especially* when using full disk encryption.  Instead of wasting CPU cycles encrypting your hard drive swap, why not use them to compress a ramdisk swap?

---

### Post by LodeRunner on 2009-05-11
Mrsteveman:

Installed Ubuntu second, made sure it didn't touch the MBR and I'm still getting nothing when I hit escape at the TC bootloader. It says that there aren't any other bootable partitions... well no crap, YOU are the bootable partition and there can only be one...

I notice someone has posted the same problem on your tech.xerces.com page.  Any way you could break this down for us a little clear-er?

---

