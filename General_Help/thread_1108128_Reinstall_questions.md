---
title: "Reinstall questions"
date: 2009-03-27
forum: General Help
---

### Post by Renigade on 2009-03-27
Please Note: Absolute Linux/Ubuntu Noob here.:lolflag:

I currently have Windows XPproX64 installed on my C drive(500GB 32bit SATA. I added a second hard drive (80gb IDE) and installed Ubuntu 8.04 X64 on it. 
I would like to take the second drive out (because I need it elsewhere) and just dual boot on my Seagate 500GB Sata.

I am not looking for people to tell me everything I need to do with step by step directions. I just need advise on how best to go about what I want to do.

1)what is the best uninstall/reinstall method?
2)Can this be done without reinstalling Windows?
3)I just switched from a Nvidia 8600GTS card to an ATI 4870 VaporX so I don't know if there will be driver issues yet as I have not tried to run ubuntu sense the switch.(dont know if this is important or not.)
4) I would like for windows to boot first.

---

### Post by mikewhatever on 2009-03-27
> **Renigade said:**
> 

1)what is the best uninstall/reinstall method?

There is no uninstall, simply delete/format the partition. To install on Seagate, you'd have to resize one of the existing partitions.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

> 2)Can this be done without reinstalling Windows?

Yes.

> 3)I just switched from a Nvidia 8600GTS card to an ATI 4870 VaporX so I don't know if there will be driver issues yet as I have not tried to run ubuntu sense the switch.(dont know if this is important or not.)

No idea.

> 4) I would like for windows to boot first.



Not a problem.

---

### Post by gorucan on 2009-03-27
> **Renigade said:**
> Please Note: Absolute Linux/Ubuntu Noob here.:lolflag:

I currently have Windows XPproX64 installed on my C drive(500GB 32bit SATA. I added a second hard drive (80gb IDE) and installed Ubuntu 8.04 X64 on it. 
I would like to take the second drive out (because I need it elsewhere) and just dual boot on my Seagate 500GB Sata.

I am not looking for people to tell me everything I need to do with step by step directions. I just need advise on how best to go about what I want to do.

1)what is the best uninstall/reinstall method?
2)Can this be done without reinstalling Windows?
3)I just switched from a Nvidia 8600GTS card to an ATI 4870 VaporX so I don't know if there will be driver issues yet as I have not tried to run ubuntu sense the switch.(dont know if this is important or not.)
4) I would like for windows to boot first.
Try using gparted live cd to manage partitions. Don't forget to make 2 times your ram of SWAP partition.

Your graphic card is fine. Ubuntu will need a good driver for it i think.

You can reorder boot list later when you install ubuntu. Find it somewhere on forums, i forgot where it is, sorry. 

Google for:

How to change boot order ubuntu.

---

### Post by coffeecat on 2009-03-27
One thing to add: when you take the second drive out you will not be able to boot into Windows (temporarily). That's because the Windows mbr has been replaced by the GRUB bootloader and some of the executables for that are in the /boot/grub folder of your Ubuntu root partition.

But don't worry, you'll still be able to use the live CD to re-partition your main drive, and when you reinstall Ubuntu onto the new partition(s) on the main drive using the live CD, GRUB will be reinstalled with a dual-boot menu and you'll be able to boot into Windows again. Whew! :wink:

---

### Post by Renigade on 2009-03-27
Thanks guys for the quick response noob rescue! :)

---

