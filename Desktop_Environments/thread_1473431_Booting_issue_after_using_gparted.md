---
title: "Booting issue after using gparted"
date: 2010-05-05
forum: Desktop Environments
---

### Post by havenoname on 2010-05-05
After using Gparted to create a new partition on my hard drive, the system(lucid) sometimes doesnt boot properly and sometimes it does boot correctly .. 
 
This is how it looks now:

[IMG]http://i44.tinypic.com/24l53zp.png[/IMG]


So the pc starts up .. and just before you (normally) see the ubuntu logo i see a row of sentences passing by fast, and then the screen becomes black.

---

### Post by marcusjames on 2010-05-05
Try sudo install-grub /dev/sda in a terminal. Please let us know how u get on.

---

### Post by dabl on 2010-05-05
If you added a partition before/in front of the partition that has Ubuntu on it, then you have changed the /dev/sdxx number of all following partitions.  That could mess up booting.

If you press "e" on the boot menu (assuming you see a boot menu), then you can remove the "quiet" option from the kernel boot line -- that will help you see boot messages.

---

### Post by havenoname on 2010-05-05
> **marcusjames said:**
> Try sudo install-grub /dev/sda in a terminal. Please let us know how u get on.

thanx for your help..
the command doesn't work?
And what does it do exactly?

---

### Post by havenoname on 2010-05-05
> **dabl said:**
> If you added a partition before/in front of the partition that has Ubuntu on it, then you have changed the /dev/sdxx number of all following partitions.  That could mess up booting.

If you press "e" on the boot menu (assuming you see a boot menu), then you can remove the "quiet" option from the kernel boot line -- that will help you see boot messages.


No that is not the case, ubuntu is still in the first one .. and in the second partition i only have some files on it(so no other operating system)

i will try the ''e'' thing .. thnx

---

### Post by havenoname on 2010-05-05
I just figured out that i dont have a boot menu ..

---

### Post by havenoname on 2010-05-07
[COLOR="blue"]**no more ideas, guys?**[/COLOR]

---

### Post by efflandt on 2010-05-07
What motherboard do you have?

You might check out the following.  But not sure if that boot parameter is different in your native language.

I have an older Athlon64 HP desktop (from 2004) with Asus motherboard, and I could not get 10.04 LTS to boot on that from a USB hd until I recreated partitions from 9.10 and used the **partman/alignment=cylinder** boot parameter on the install CD.  But in that case grub2 could not even identify the (ext3) file system on a 500 GB USB drive (unknown filesystem), or file not found on 160 GB USB drive, even though the USB drives booted fine on 2 different laptops. Now I can boot 64-bit 10.04 LTS from the 160 GB USB drive on the HP, but have not tried that on the 500 GB drive yet.

---

### Post by oldfred on 2010-05-08
If you only have Ubuntu you will not see the menu unless you hold down the shift key from the end of BIOS boot. Then you should get the menu. First try the recovery mode. Then you can try the edit menu choice. It sounds like you are past grub booting and into other boot issues often video related but it could be anything.

---

### Post by b.bugra on 2010-05-08
Did you try pressing Ctrl+Alt+F7 ?

Almost exact thing happened to me on my first experience with gparted. I could see Ubuntu booting normally but I couldn't see login screen. Then I realized somehow it does not switch to tty7.

---

### Post by havenoname on 2010-05-08
> **efflandt said:**
> What motherboard do you have?

You might check out the following.  But not sure if that boot parameter is different in your native language.

I have an older Athlon64 HP desktop (from 2004) with Asus motherboard, and I could not get 10.04 LTS to boot on that from a USB hd until I recreated partitions from 9.10 and used the **partman/alignment=cylinder** boot parameter on the install CD.  But in that case grub2 could not even identify the (ext3) file system on a 500 GB USB drive (unknown filesystem), or file not found on 160 GB USB drive, even though the USB drives booted fine on 2 different laptops. Now I can boot 64-bit 10.04 LTS from the 160 GB USB drive on the HP, but have not tried that on the 500 GB drive yet.

Ive got asrock but i also have a cd with graphical drivers for asus.. asus=asrock?

.. i'm still able to boot sometimes after restarting the pc one or two times.

So what do i have to do exactly?

---

### Post by havenoname on 2010-05-08
> **oldfred said:**
> If you only have Ubuntu you will not see the menu unless you hold down the shift key from the end of BIOS boot. Then you should get the menu. First try the recovery mode. Then you can try the edit menu choice. It sounds like you are past grub booting and into other boot issues often video related but it could be anything.

.. i tried the recovery mode. And i already turned on the boot menu. I see messages passing by ..but they go to fast. Is there a way to save it?

That's right it already passed the grub booting... i think you are right, sometimes if the system does start i see the screen a bit misformed and then it corrects itself.

 I must figure out how to get that message befoor the black screen, saved?

---

### Post by havenoname on 2010-05-08
> **b.bugra said:**
> Did you try pressing Ctrl+Alt+F7 ?

Almost exact thing happened to me on my first experience with gparted. I could see Ubuntu booting normally but I couldn't see login screen. Then I realized somehow it does not switch to tty7.

no ubuntu isn't booted yet.. you see a " **[SIZE="5"]_[/SIZE]** " on the top at the left side and then the message passes by and then it turns black...

---

### Post by havenoname on 2010-05-08
**oh yeah.. thanks for thinking along...!**

---

### Post by oldfred on 2010-05-08
Did the recovery mode offer video settings or get you to update the system?

On my system I had to edit the kernel line and add nomodeset to get into a low quality video mode. After update to video driver - nvidia for me, it worked fine.

---

### Post by havenoname on 2010-05-11
> **oldfred said:**
> Did the recovery mode offer video settings or get you to update the system?

On my system I had to edit the kernel line and add nomodeset to get into a low quality video mode. After update to video driver - nvidia for me, it worked fine.

I tried the recovery mode before.. but that didn't help


BTW. I started up the system a couple of times and now it starts up correct..

[COLOR="Red"][SIZE="5"]It only gives me this error now : The disk drive for UUID= [COLOR="Black"]some letters and numbers[/COLOR]  is not ready yet or not present. 
[/SIZE][/COLOR]

---

### Post by oldfred on 2010-05-11
this sounds like something is not quite right in fstab. Are you mounting external drives or network drives?

Post a copy of /etc/fstab.

---

### Post by havenoname on 2010-05-11
> **oldfred said:**
> this sounds like something is not quite right in fstab. Are you mounting external drives or network drives?

Post a copy of /etc/fstab.


Thanks oldfred .. it seems to be fixed after altering the fstab

There was a problem with the swap, for the ones with the same problem see this thread:
[http://ubuntuforums.org/showthread.php?t=51174&page=2](http://ubuntuforums.org/showthread.php?t=51174&page=2)

---

