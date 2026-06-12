---
title: "New to Ubuntu + Dell Vostro 1400"
date: 2008-05-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pchitrada on 2008-05-30
Hi all,

I installed ubuntu 8.04 on my Dell Vostro 1400 using Wubi-8.04 with dual boot with Vista

In[COLOR="Red"]tel Core 2 Deo  T5470 @1.60 GHz
3 GB Ram
NVIDIA GeForce8400gs
Broadcom Netlink(TM) Fast Ethernet
Dell Wireless 1490 Dual Band WLAN
[/COLOR]

every thing was smooth, but my wireless is not connecting. 
when i checked the hardware drivers list, NVIDIA is only showing in the list. It is showing the network icon on the top right corner but after entering network details, its showing as scanning but not able to connect to router.

Sound is working. But no internet.I  followed few articles in this forum but no luck. Please help me out guys.I am counting on you

Never quit - praveen:confused:

---

### Post by Aearenda on 2008-05-30
Presumably it will work if wired, rather than wireless.

Linux uses chipset drivers rather than a Dell branded driver. ```
lspci | grep Ethernet
``` should tell us what is needed - can you post the output from that command?

---

### Post by Aearenda on 2008-05-30
BTW, have you tried this: [http://ubuntuforums.org/showthread.php?t=811248](http://ubuntuforums.org/showthread.php?t=811248)

---

### Post by pchitrada on 2008-05-30
thanks for you reply, i tried the code u give the output is

lspci | grep Ethernet

09:00.0 Ethernet controller: Broadcom Corporation Netlink BCM5906M Fast Ethernet PCI Express (rev 02)

and for 

lspci | grep Network

0c:00.0 Ethernet Network: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)


after trying the second link you have given by connecting to LAN, after restart now my sound also not working.

please let me know what to do

---

### Post by Aearenda on 2008-05-30
Well, since your lspci output didn't match the lspci mentioned in that link, it probably didn't help. To reverse that change, do```

sudo apt-get remove linux-backports-modules-hardy-generic
``` and reboot.

Your wireless uses the BCM4312 rev 01 chipset, so this is probably going to get very messy! I would try this first: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
This has Hardy instructions, and you should use step 2b when you get to that point. This will use the Windows driver and Ndiswrapper, a tool that makes Windows wireless drivers work in Linux.

If that doesn't work, I would see if [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) has any useful variations.

If you don't want to use the Windows driver, try [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754). This post [http://ubuntuforums.org/showpost.php?p=4806915&postcount=4](http://ubuntuforums.org/showpost.php?p=4806915&postcount=4) suggests that your card *should* work this way.

Good luck!

EDIT: Actually, I'd try the third suggestion first ([http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)), since there is less work in it.

---

### Post by pchitrada on 2008-05-30
it working,wireless is working,

 i tried the third suggestion

i really thank Aearenda for helping me out

 but no sound 

it is 'No volume control GMstreamer plugin and/or device found'

Thanks  

Never Quit - praveen

---

### Post by pchitrada on 2008-05-30
it working,wireless is working :guitar:,

 i tried the third suggestion

i really thank Aearenda for helping me out

 but no sound 

it is 'No volume control GMstreamer plugin and/or device found'

Thanks  

Never Quit - praveen:confused:

---

### Post by Aearenda on 2008-05-30
Ok, the sound thing is my fault - assuming it was the backports idea that broke it - after removing the backports meta-package, I should have also told you to remove the packages it depends on. This can be done by either 
```
sudo apt-get autoremove
```
or better by ```
sudo apt-get remove linux-backports-modules-`uname -r`
```
The latter is safer since autoremove will possibly remove other things and I'd rather just change one thing at a time here.

Note the back-quotes - they are important. This causes the output from the command "uname -r" to be inserted, thus completing the name of the package with your running kernel version.

---

