---
title: "Dual Boot with Vista"
date: 2008-12-06
forum: General Help
---

### Post by Pappalnator on 2008-12-06
I have a Dell XPS 720 Desktop that I really think hates me right now.

It comes preinstalled with Vista Home Premium. It has a 500GB Hard Drive, so I say "Hey, lets dual  boot Intrepid Ibex".

So I Burn the CD, plug it in while Vista is running, and install it like a windows application. Well, when I try to boot Intrepid, it comes up with this
> Loading, Please Wait...

Busybox blah blah type help for a list of functions or something

I type help and type in every single command like boot, boot ubuntu, go, continue and none of it works and I am forced to type reboot and go back into Vista (arrgghh). Can anyone help me get Ubuntu working?

I've tried both 32 and 64 bit Intrepids.

Specs:
Vista Home Premium 32bit
2GB RAM
Intel Core 2 Duo CPU E6850 running @ 3.00 GHZ 3.00GHZ

When running Ubuntu isntall as a windows application I chose 30GB install and Ubuntu

Thanks in advance

---

### Post by Pappalnator on 2008-12-06
Bump!

---

### Post by Pappalnator on 2008-12-06
C'mon guys, I need a little help :(

---

### Post by TeXtonyx on 2008-12-06
Supposing that you have the Ubuntu live cd for your platform, often
I386 but sometimes x64, there is a different install approach.

You go into bios (often when you boot up it says hit Delete or
some other key) and you set your boot order to cdrom first.
There is another kind of install called Wubi, that installs 
Ubuntu into the Windows partition. You need to have right cd
for that, the usual one installs to an unallocated partition
on your hard drive. That means you have to make a space for it.

Use Gparted to resize your XP partition, say you shrink it by
100GG, then that will be the size of the new Ubuntu partition.

When you boot with the cd in the cdrom, proceed with the Ubuntu
installation to drive, and when it comes to deciding where to
install Ubuntu, pick 'largest continuous free space (guided)'
which will keep XP safe. That space^^^ is the unallocated space
you just created by resizing the XP partition, not unused space
within the XP partition; Ubuntu goes outside the XP partition.

You can proceed from there with the defaults which will install
grub to the MBR which once in awhile causes a problem. Then you
would be booting XP from the Ubuntu grub bootloader.

My practice is to during the installation at Step 7, Advanced,
to choose to install grub to the /boot partition, which leaves
the MBR alone for XP. I download a free program called Bootpart
which creates a 512 byte ubuntu.bin in C:\ and automatically
writes Ubuntu to your boot.ini boot options. I think you could
also download Easybcd which has a GUI and add Ubuntu that way.

---

### Post by Pappalnator on 2008-12-07
Thanks for your reply. However:
-I am running Vista, not XP (may be the problem)
-During the CD Boot (I have done it) Ubuntu Installer will not see the unallocated space. The only options are manual or guided-use whole partition. Well, not very useful.

And yes, I did resize Vista partitions by using Shrink Volume.

And I think I may have my problem. I have seen in another post that the main problem was that there were already 4 primary partitions, so Ubuntu Installer could not make a new one out of unallocated space, so it eliminated that option.

Anyone know how to either:
-Make an extended partition to install Ubuntu
OR
-Use an existing partition to install Ubuntu (if Im correct, Vista is only using one, so I have to get to one of the other 3?)

Thanks guys.

---

### Post by Pappalnator on 2008-12-07
Bump

---

### Post by falcon61102 on 2008-12-07
Load up the LiveCD and then open up a Terminal by going to Applications>Accessories>Terminal.  Once that loads, run the following command and post it here:
```
sudo fdisk -lu
```

This will list your partitions.

To format the partitions in preparation for installation it is recommended that you use gParted which comes installed on the LiveCD.  Go to System>Administration>Partition Editor.  This is similar to the Vista version but more powerful.  Keep in mind that you are going to need to create two partitions for this installed.  One will be your primiary (root) partition, the other will be a SWAP partition that is usual about twice the size of your RAM.  

Post the results from the code above and we can get you set on the partitioning.

---

