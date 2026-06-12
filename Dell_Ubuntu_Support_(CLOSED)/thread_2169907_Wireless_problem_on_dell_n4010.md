---
title: "Wireless problem on dell n4010"
date: 2013-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaycen2 on 2013-08-24
Hello all, I'm new to Linux (sort of) and I'm having some problems with my wireless. My drivers are not proprietary, and the controller is broadcom BCM4313. I know there is a sticky about said controller in another thread, but its in a different version of Ubuntu. I'm running 12.04 LTS. Any help will be greatly appreciated.

---

### Post by varunendra on 2013-08-24
Welcome to the forums jaycen2 !

Please post the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
apt-cache show bcmwl-kernel-source | grep -i version
```

---

### Post by jaycen2 on 2013-08-24
Thanks for the welcome!  

Outputs are as follows: 
3.8.0-29-generic x86_64

Network controller: Broadcom BCM4313 [14e4:4727]
Kernel modules: bcma
Ethernet controller: Atheros communications inc AR8152 [1028:0456] 
Kernel driver in use: atl1c

eth0 no wireless extensions
lo     no wireless extensions

Version:  6.20.155.1+bdcom-0ubuntu0.0.1

Sorry for the slow response, I'm on a smartphone right now due to only having one computer available right now

---

### Post by jaycen2 on 2013-08-24
Forgot to mention I'm also dual-booting with windows 7

---

### Post by varunendra on 2013-08-24
> **jaycen2 said:**
> Outputs are as follows: 
**3.8.0-29-generic** x86_64
Have you manually installed the above kernel ? Because as much as I am aware, 12.04 doesn't use kernel 3.8x yet. But since 12.04.3 is out, I may be wrong.

Also, you did not post the output of "rfkill list all". Please do so now. For now, I am assuming your wifi is NOT hard blocked (if it is, post back without following the suggestion below).

> Network controller: Broadcom BCM4313 [14e4:4727]
Kernel modules: **bcma**
As a test, please try (without rebooting) -
```
sudo modprobe -rfv bcma
sudo modprobe -v brcmsmac
```
Does it activate your wireless?

---

### Post by jaycen2 on 2013-08-24
Well the sudo commands have indeed brought my wireless back, but I'm not sure if it will stay when I reboot. 
Nothing happened when I did the killall, it just created a new command line under it.
As for the kernel, all I did was install Ubuntu on a 15g partition.  I don't think my wireless is hard blocked, because when I boot into windows, wireless does indeed work, its only when I'm in Ubuntu.

---

### Post by varunendra on 2013-08-24
> **jaycen2 said:**
> Well the sudo commands have indeed brought my wireless back....
Okay, let's just focus on that part for now. Please blacklist the driver "bcma" and see if "brcmsmac" loads automatically on next boot. To blacklist bcma -
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and see if the wireless works on next boot.

Also, run the following command (after running above command and rebooting) and see which of the two drivers is loaded -
```
lsmod | grep -e bcma -e brcmsmac
```

We want only brcmsmac in the output of above command, and NOT bcma.

---

### Post by jaycen2 on 2013-08-24
Okay I rebooted, and wireless is gone. I tried the second command and nothing happened. I'm guessing I don't have the package. Its "modules-init-tools"

---

### Post by varunendra on 2013-08-24
Please run again-
```
sudo modprobe -v brcmsmac
```

Does it connect?

---

### Post by jaycen2 on 2013-08-24
Yes it does connect

---

### Post by varunendra on 2013-08-24
Hmm.. it should have loaded automatically. Anyway, let's make it load automatically the other way.

Please do -
```
echo "brcmsmac" | sudo tee -a /etc/modules
```
..then reboot and check if brcmsmac loads this time -
```
lsmod | grep brcm
```
Moreover, if it connects.

If it does, everything's done! If not, we may need to fix a couple more things.

---

### Post by chili555 on 2013-08-24
I hope Varun won't mind if I lend a little help.>  Please blacklist the driver "bcma" and see if "brcmsmac" loads automatically on next boot. To blacklist bcma -
Code:

echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

In fact, bcma is a dependency of the correct driver for your device brcmsmac:```
$ modinfo brcmsmac
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DCFCFF03DB5656E4F6EBB6F
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,[COLOR="#FF0000"]bcma[/COLOR],brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
```So please undo the blacklist:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove this line:```
blacklist bcma
```Proofread, save and close gedit. Now I am troubled by:> Version: 6.20.155.1+bdcom-0ubuntu0.0.1Let's see if we can remedy that:```
sudo apt-get remove --purge bcmwl-kernel-source
```After all this is done, please reboot and let us have your report.

---

### Post by jaycen2 on 2013-08-24
Bumping, it still does not work after a reboot.   Please help me, I've been working on this for hours now.

---

### Post by jaycen2 on 2013-08-24
> **chili555 said:**
> I hope Varun won't mind if I lend a little help.In fact, bcma is a dependency of the correct driver for your device brcmsmac:```
$ modinfo brcmsmac
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DCFCFF03DB5656E4F6EBB6F
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,[COLOR=#FF0000]bcma[/COLOR],brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
```So please undo the blacklist:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove this line:```
blacklist bcma
```Proofread, save and close gedit. Now I am troubled by:Let's see if we can remedy that:```
sudo apt-get remove --purge bcmwl-kernel-source
```After all this is done, please reboot and let us have your report.

I have purged the kernel, but when I reboot, I have no wireless.  I have to redo what Varun says, which is:
sudo modprobe -v brcmsmac
After that I do have wireless.

---

### Post by chili555 on 2013-08-24
Let's have a look at:```
cat /etc/modules
```

---

### Post by jaycen2 on 2013-08-24
Well just for giggles, I tried the purge again, and it does indeed work, but I'll go and do that.

Code output:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc
wl

---

### Post by chili555 on 2013-08-24
Please do:```
gksudo gedit /etc/modules
```Remove wl and add brcmsmac; thus:```
Code output:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc
brcmsmac
```Proofread carefully...twice, save and close gedit. You should be all set. Post back if not and we'll be happy to help.

---

### Post by jaycen2 on 2013-08-24
Gonna reboot and see if it helped.

---

### Post by jaycen2 on 2013-08-24
Wow thank you so very much!  Been trying to figure this out for hours, since last night!  
Now, I'm sure this is easy to fix, but every once in a while, the "Wired network is disconnected" balloon will pop up every few minutes or so.  You could imagine how annoying this is.  Is there any way to fix this as well?

---

### Post by chili555 on 2013-08-24
Glad it's working! Please mark the thread Solved. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

As for your ethernet problem, I suggest you start a new thread either here or on Networking and wireless and include:```
nm-tool
ifconfig
lspci -nn | grep 0200
```

---

### Post by varunendra on 2013-08-24
> **chili555 said:**
> In fact, bcma is a dependency of the correct driver for your device brcmsmac:```
$ modinfo brcmsmac
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DCFCFF03DB5656E4F6EBB6F
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,[COLOR="#FF0000"]bcma[/COLOR],brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
```
Ouch !! Was ringing somewhere in my head ever since I suggested the blacklist, but the output from my older kernel deceived me -
```
modinfo brcmsmac
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     FE858A4853BCA5C5A84D63C
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-36-generic SMP mod_unload modversions 
```
Thanks for the rescue sir ! :P

However, the "apt-cache show.." output didn't trouble me, since it only lists "Available" packages, even if they are not installed. I was expecting to get two available versions, of which I would have tried the older one (5.xx) had the brcmsmac failed.

But in the last, learnt my lesson (the 100th time) - "Never take things for granted" *(and probebly use the wireless_script more often..)*:P

---

### Post by chili555 on 2013-08-25
> Thanks for the rescue sir !I responded in a PM.

---

