---
title: "Need help with Dell Inspiron 1525 and Ubuntu"
date: 2008-01-12
forum: Dell  Ubuntu Support
---

### Post by kingleer on 2008-01-12
I just installed ubuntu 7.10 (the 64-bit version),a nd everything except for wifi works perfectly. I installed ndiswrapper, and tried to use ndiswrapper to install the wireless driver. I was able to install the driver successfully successfully. But when I type in iwconfig, I get the results shown in the picture attached at the bottom of my post. 

I tried checking out - 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c9037d4dac23680f0939e488c2291413ce831ef3](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c9037d4dac23680f0939e488c2291413ce831ef3)

When I enter 

lspci | grep Network 

in the terminal I get

0b: 00.0 Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev-01) 

I used the driver I found here for ndiswrapper

[http://forum.x-drivers.com/index.php?showtopic=2162&pid=21285&st=0&#entry21285](http://forum.x-drivers.com/index.php?showtopic=2162&pid=21285&st=0&#entry21285)

In particular this driver

[http://x-drivers.ru:81/drivers/wireless/broadcom/www.x-drivers.ru_broadcom_v4.150.22.0.zip](http://x-drivers.ru:81/drivers/wireless/broadcom/www.x-drivers.ru_broadcom_v4.150.22.0.zip)




No luck getting my wireless card working. I'm a pretty big linux noob, but I've been using Ubuntu as my main and only OS since 2006. I've been able to get my wireless cards working in the past using ndiswrapper, but I just got this Dell Inspiron. 

Help would be greatly appreciated. Thanks in advance.

---

### Post by kingleer on 2008-01-12
Here's that picture with my iwconfig output by the way.

---

### Post by natehall on 2008-01-12
I think the problem is lack of drivers that support 64 bit architechure. Dell preloaded my 1420N ( a 64 bit chip) with 32 bit Ubuntu. I wondered why for awhile but I found out eventually too many things are only configured for 32 bits and not 64 bits yet. I can remember when only super-computers ran a 64 bit bus !

---

### Post by demoric on 2008-02-03
I too have a Dell insprion 1525 and have had an terrible time trying to get the wireless networking to work.  (I literally spent 14+ hours  and trying differentt drivers)

All in all every single one I tried would seem to work, but I couldn't use the Network applett in system > administration.  However the last driver I used was [b][http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
[/b][I](but it's basically the same as the other's I've tried [http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
)[/I]

When all was said and done however I believe it boiled down to just manually setting up my wireless connection. 
**[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)**

---

### Post by 2GooD on 2008-02-21
Has anyone tried ubuntu-dell-1525n-intelvideo-reinstall.iso from [http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/) yet?

I'm trying tonight and posting my experiences in the [Dell category of my blog](http://www.divideandconquer.se/category/dell/).

\David

[http://www.divideandconquer.se/](http://www.divideandconquer.se/)

---

### Post by xxxx1234 on 2008-02-21
> **demoric said:**
> I too have a Dell insprion 1525 and have had an terrible time trying to get the wireless networking to work.  (I literally spent 14+ hours  and trying differentt drivers)

All in all every single one I tried would seem to work, but I couldn't use the Network applett in system > administration.  However the last driver I used was [b][http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
[/b][I](but it's basically the same as the other's I've tried [http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
)[/I]

When all was said and done however I believe it boiled down to just manually setting up my wireless connection. 
**[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)**

Your guys don't need to do any of these to get your wireless work on 1525. Just need to do the following:(if you want to dual boot vista and ubuntu).

1. Download the 1420N iso with X3100 support iso from Dell site.
2. Burn the iso and boot up the DVD.
3. Select live to run live CD.
4. After live CD is run, click the install icon.
5. Install the Darwin installer to /root.
6. After installation connect the ethenet cable, this will get you online.
7. Go to enable the wireless connection and SELECT - GET THE DRIVER FROM INTERNET. Ubuntu will  get the driver and your wirless connection will be wokring!
8. That is it, you get your dual boot vista and ubuntu.

Good luck.

---

### Post by Papa-san on 2008-03-01
Has anybody done this?
I have 1525's arriving on Monday, and it would be a refreshing change to have a system be dual boot without hours and hours of endless entertainment...

---

### Post by Papa-san on 2008-03-03
I have tried to find this file at the dell site, and cannot seem to find it. Could you provide a link? Please?

Thanks, (Two of the three arrived today! :D

---

### Post by CloudFX on 2008-03-03
If ANY of you with a Dell Inspiron are still having troubles installing your wireless driver, your in luck. I got my wireless working effortlessly in about a minute. Dell has recently released firmware which allows your wireless cards to support Ubuntu. 

Here's what to do:
1. Open up System > Administration > Restricted Drivers Manager
2. Under the firmware category, you will see something to do with a Broadcom driver. Check that box.
3. You will be prompted to either get the firmware from a disk, or to download it. The site to download it from is given for me. Select it, and the wireless card should work!

It certainly did for me [img]http://ubuntuforums.org/images/smilies/icon_smile.gif[/img]

---

### Post by TCTopCat on 2008-06-10
Hey I have nothing visible in my drivers section(i'm using 8.04lts so no restricted drivers menu). Can you post the link for firmware download please?

---

### Post by MindZEye on 2008-06-18
My wireless appears to have been broken by the 2.6.24-18 and upwards kernels, as KNetworkManager spins its wheels at:
```

"Activation stage: IP configuration started."

```

If I downgrade to the 2.6.24-16 kernel it works again fine, but that seems like a ludicrous thing to do long term.  Currently using the wl driver as that was working fine for several months, I don't appear to be able to get ndiswrapper to work through the various methods shown around the net, with this kernel either.

Here's the relevant section from "lshw -C network":
```
  
*-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:4d:63:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

Does anyone have any suggestions as to how to sort this?

---

