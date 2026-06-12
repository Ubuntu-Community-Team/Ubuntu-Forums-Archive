---
title: "Insprion 14z - UEFI boot hangs at purple screen if NIC activated"
date: 2012-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mlaverdiere on 2012-12-23
Here's my weird problem, with a UEFI Ubuntu 12.10 64 bits installation on an Inspiron 14z ultrabook with an integrated Atheros AR8162 ethernet card (NIC).

If the AR8162 card is enabled in BIOS, Ubuntu won't load, as it will hang in a blank purple screen or, in recovery mode, at "loading initial ramdisk". If the AR8162 card is disabled, it will boot just fine. The problem is that I need an ethernet connection...

What is strange is that I'm able to boot Ubuntu in legacy mode with the AR8162 enabled in BIOS and this card is working just fine with the alx module available in compat-wireless package (see: [http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162/231715#231715](http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162/231715#231715)). The only thing is that I want to keep dual booting with Win8, so UEFI Grub installation is mandatory.

Any idea someone on how to boot Ubuntu 12.10 in UEFI mode, with a working AR8162 card?

Thanks.

---

### Post by oldfred on 2012-12-23
There are some bug reports with work arounds.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046435](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046435)

---

### Post by mlaverdiere on 2012-12-23
Thanks oldfred, but the problem is not that I can't make the AR8162 work (again, it works pretty well with alx module when I boot in BIOS legacy mode).  The problem is that I have to disable the card in BIOS if I want to boot in UEFI mode.

I'm just wondering if there could be a Kernel boot parameter that I could use to tell the kernel not to probe for this card and/or not to activate it, as I may be able, if the boot completes successfully, to activate it later, just by modprobing the alx module...

---

### Post by mlaverdiere on 2012-12-31
Bump!

---

### Post by oldfred on 2012-12-31
Are there any settings in UEFI menu?

I think both BIOS or UEFI write some info in RAM or drive for system to use when booting. Is it then UEFI not writing the correct or same info or Ubuntu cannot find it as it is somehow a bit different? Seems like a bug somewhere?

Do you get the same info from these from both systems or is there some subtle differenece?

lspci -v
dmesg | grep eth
# Plug in Ethernet cable and see if errors:
dmesg | tail -n10
# Check by chipset:ie e1000e
sudo lsmod | grep e1000e

---

### Post by takuie on 2013-01-04
Try updating bios, dell doesn't always ship with latest version for some reason.

---

### Post by rktesser on 2013-05-08
Any news on this issue?
I have the last bios version (from 2 days ago), and this problem is still present.

There's bug [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1093472](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1093472) , but no hint to a possible solution (besides disabling secure boot) until now.

---

### Post by rktesser on 2013-05-08
Sorry. Double post. I don't know how to delete it.

---

### Post by diego8 on 2014-02-05
Hi, I have the same problem. 


I have an Inspiron 14z with windows 8 pre installed. I installed ubuntu 13.10, but I have to run it in the bios disabled the network card. 


Ahola, I have the same problem. 


I have an Inspiron 14z with windows 8 pre installed. I installed ubuntu 13.10, but I have to run it in the bios disabled the network card. 


Someone find the solution to this problem?

---

### Post by oldfred on 2014-02-05
This applies to many versions of Dell's not just precision models.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

      
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

 Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)

---

