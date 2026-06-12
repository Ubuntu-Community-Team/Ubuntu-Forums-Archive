---
title: "Help needed installing 7.10 as encrypted partition"
date: 2008-12-19
forum: Desktop Environments
---

### Post by SimbaSpirit on 2008-12-19
I'm pretty new to the concept of encrypting an entire partition, much less an OS.

From what I've read it seems that I can keep everything but the bootloader inside an encrypted partition, but I can't seem to find a good how-to online no matter how much I google, which leads me to believe I'm mis-informed.

This is the setup I'm aiming for:
sda1 = Vista (already installed)
sda2 = ntfs partition (common files for both OS's)
sda3 = encrypted ubuntu 7.10
sda4 = swap

I'm using the alternate (text-based) install CD and it doesn't sound capable of encrypting a partition and installing ubuntu to it. What's the closest I can come to this? Do I need a fifth partition for parts of ubuntu to reside unencrypted?

Currently my proposed setup reads:

#1 Primary 107GB ntfs
#2 Primary 284GB ntfs
#3 Primary 105GB B K crypto not active
#5 logical 3GB f swap swap

When I try to proceed it says "No root file system is defined", because I can't choose to install ubuntu to #3.

Any thoughts?

Thanks,
-SS

---

### Post by SimbaSpirit on 2008-12-19
Has anyone successfully done this before?

---

### Post by mojo90 on 2008-12-19
To create a encrypted partition, you need to use the alternate-cd

The partition layout should look like this:
Vista
NTFS
/boot (~100mb)
Encrypted partition
____LVM
________Swap
________/

The encrypted partition contain a LVM and the LVM contain the 2 others partitions so only 1 password is needed to boot the OS

---

### Post by SimbaSpirit on 2008-12-19
Thanks for the reply!

When I create it as you have laid out, it complains that I haven't defined a root file system.

How can I specify in the alternate installer to put / in (encrypted->lvm->/)? I can choose from:
physical volume for encryption
physical volume for LVM
Ext3 journaling file system (which I can make /)

Based on what you're saying, physical volume for encryption sounds like the correct choice, what should I be choosing??

Thanks,
-SS

---

### Post by mojo90 on 2008-12-20
Step by step instructions:

Create the /boot partition
Create the other partition (the encrypted one) 
Select "physical volume for encryption"
Select "done setting up the partition"
Select "configure encrypted volumes"
Then enter the encryption passphrase
The partitioner will change and change the new ext3 partition to a  "physical volume for LVM"
Validate and go back to the main partitioner screen
Select "configure the Logical Volume Manager"
Select "create a volume group"
Enter a name for the volume group (example : mvg)
Select the device "/dev/mapper/sda?_crypt"
Select "create a logical volume"
Select the volume group (mvg)
Enter a name for the volume group (swap)
Choose the amounts of space for the swap and validate
Select "create a logical volume" and this time use the rest of the remaining space, this will become the / 
Validate and go back to the main partitioner screen

Finally, you can change the 2 new partition to their right type (swap and ext3)

Enjoy

---

### Post by SimbaSpirit on 2008-12-20
Very detailed, thanks!

---

