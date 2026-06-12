---
title: "dell inspiron broadcom 4401 driver and setup"
date: 2009-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geck0man on 2009-07-28
I just installed Ubuntu on a Dell inspiron 2400 which was running XP. I did a full install over the entire HDD, so Ubuntu is the only OS now. I can't seem to get the ethernet card working. Can someone please tell me where I can get the drivers for the Broadcom NIC 4401 and walk me through setting it up. I am completely new to Ubuntu and Linux.

---

### Post by FirstByté on 2009-07-28
Which distro are you using? This appears to be a problem with distros lower than Ubuntu 8.10. However you can follow this steps on these pages (*sorry I don't wanna type to avoid duplication*):

[http://ubuntuforums.org/showpost.php?p=125537&postcount=1](http://ubuntuforums.org/showpost.php?p=125537&postcount=1)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

Good luck.

---

### Post by geck0man on 2009-07-29
Thanks FirstByte, but the instructions you point to are for the problems with wireless networking and wireless card. Your attempt is appreciated, but there seems to be a lot of advice on fixing the wireless problem. I did check.

I just have a plain old 10/100 ethernet card. I can't seem to find suitable instructions on setting up the NIC.

I am running Ubuntu 9.04.

Any additional advise?

---

### Post by FirstByté on 2009-07-30
Sorry for the presumption!:P I'm used to hitting problems with Wireless NICs which I thought works out of the box.
======

*Excerpts from [http://www.broadcom.com/support/ethernet_nic/4401.php](http://www.broadcom.com/support/ethernet_nic/4401.php) *

**[Download Link here]("http://www.broadcom.com/support/ethernet_nic/driver-sla.php?driver=4401-Linux")** 

[B]If you prefer the GUI method... 
[/B]
* Go to the location you saved the zip file and double-click or open it anyhow
* Go to your home directory and right-click to make a new directory and name it "***broadcom_4401driver***" of whatever is easier
* Extract the file into the folder you created "broadcom_4401driver" and further extract the files inside the "linux-1.00g.zip" into the new folder and
* Open the README.TXT file. and scroll to the section that says 
```

Building Driver From TAR File
=============================

```







**Else**


Make a directory in your home directory
```

~$ mkdir ~/broadcom_4401driver

```

copy the file "linux-1.00g.zip" that you downloaded from the Broadcom site to the new folder you created. assuming you downloaded it to the Desktop.
```

~$ cd ~/broadcom_4401driver
~/broadcom_4401driver$ cp ~/Desktop/linux-1.00g.zip ~/broadcom_4401driver

```

Install Unzip if you don't have it yet.

```

~/broadcom_4401driver$ sudo apt-get install unzip

```
and unzip it...
```

~/broadcom_4401driver$ unzip linux-1.00g.zip

```

Then carry on with the instruction as written in the README.TXT file.

<[COLOR="Red"]**Linux is case sensitive**[/COLOR]>
```

~/broadcom_4401driver$ gedit linux/README.TXT

```

***excerpts... from README.TXT***

The following are general guidelines for installing the driver.



1. Create a directory and extract the files:

   tar xvzf b44-<version>.tar.gz

2. Build the driver b44.o (or b44.ko) as a loadable module for the
running kernel:

   cd src
   make

3. Test the driver by loading it: 

   insmod b44.o
or
   insmod b44.ko (on 2.6.x kernels)

or
   insmod b44


4. Install the driver:

   make install

5. To configure network protocol and address, refer to various Linux
documentations.


==========
These info would certainly help (*for troubleshooting*):

```

~$ lspci -nn | grep -i network

```


Glad to help anytime!:popcorn:

---

### Post by whitecrow on 2013-03-18
And then none of this works!  I cd, cd, cd.  I configure, makeinstall, xyz, src...and nothing works.  It all says STOP!  

Done venting!  I installed 12.04 on a Dell Inspiron 8500 with only an ethernet port and no wireless.  No internet because I have a broadcom 4401 ethernet adapter.  On another computer, I downloaded what I think to be the proper driver but it is only available in tar.gz format.  I have been jacking with Ubuntu for years now but I've never been able to do anything with files like these.  If I had an internet connection on the laptop, I would simply...do something else.  But I don't.  Could someone maybe help me find an installer package for this driver?  I am whupped at makeinstallcd...try not to look at the Windows XP cd in the desk drawer which would solve all my problems.  Sigh!

---

### Post by mörgæs on 2013-03-19
The thread concerns obsolete Ubuntu releases so information here is likely to be of little value.

Closing the thread but feel free to open a new one in for example General Help (as this is not specific for Dell), but first I would recommend that you try installing Lubuntu 12.10 or 13.04 (beta).

---

