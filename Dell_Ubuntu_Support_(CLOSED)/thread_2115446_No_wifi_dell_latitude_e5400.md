---
title: "No wifi dell latitude e5400"
date: 2013-02-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chotchkin on 2013-02-12
Hey,  I am new to Ubuntu and have installed it on a Dell Latitude ES5400.  Ethernet works but I can't seem to get the wifi to work and help I could get to set it up would be greatly appreciated.  I am looking forward to learning to use a linux based system and learning how to fix this problem.  Thanks.

---

### Post by lincoln32 on 2013-02-12
wifi is one of the painfull parts I suspect your dell has a broadcom so lets check  click in the upper right round Icon and type terminal and open it then type lspci and copy the output here:o

---

### Post by Chotchkin on 2013-02-13
Sorry got a dumb question already.  How do you copy the output and put it here?  I can copy and paste it in the terminal but I can't paste it here.

---

### Post by lincoln32 on 2013-02-13
hold left mouse button down and drag across everything you want to copy
I is easier to start in a corner. then right click for options  pick copy
then come back here and right click paste. it will copy all the text you highlighted and paste it here. I usually recommend checking anything you 
paste here and delete usernames and passwords ect.:)

---

### Post by Chotchkin on 2013-02-13
I try that and the right mouse button dehighlights the selected text and no window pops up to select copy and paste?  I tried to just take a screen shot but I guess prnt scrn works differently with Ubuntu?  That didn't work either.  The last line of the output says 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (9rev 01)
I don't know if that is all of what you need.  I can type the whole thing out if you need.

---

### Post by lincoln32 on 2013-02-13
ok you found the issue---the drivers and firmware are not open source so they cannot be included legally. but you can install them for free
follow this guide for the BCM4312 wifi and then reboot and it should work fine

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx:p](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx:p)

11.10 (Oneiric Ocelot) - 12.10 (Quantal Quetzal)

Open a Terminal and install the bcmwl-kernel-source package:

sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

Note: If you see the message "Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed" then you are missing the appropriate generic linux-header package(s).

To test the driver (and remove the need for a computer restart) use:

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl

Allow several seconds for the network manager to scan for available networks before attempting a connection.

The bcmwl-kernel-source package should automatically blacklist the open source drivers so that the STA driver is the only one in use. However, some 11.10 users may have to manually blacklist the open source modules (please see the Known Issues section).
Back to top

---

### Post by Chotchkin on 2013-02-13
I got that message "module build for the currently...." and was followed by the following errors
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm 43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs:  Generating /boot/initrd.img3.5.0-17-generic

---

### Post by lincoln32 on 2013-02-13
I see the code was incorrectly written and now the site is down I assume to edit it and rewrite it so I just found the one and it has the addle drivers option that I have used before and may be easier for you the addl drivers are keep in different locations depending on which version of ubuntu you are using. Do not worry about the old code it did not break or add anything


[http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-card-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-card-bcm43xx)

stick with it it is worth it to use ubuntu vs winders :)

---

### Post by Chotchkin on 2013-02-16
It is finally recognizing the wifi.  The wifi light on my keyboard now lights after using synaptics.  But it still does not connect.  Auto connect is checked under the wireless tab of the networking box.  
Thank you for your help and patience by the way.  I do like Ubuntu.  I have not found anything so far I would rather use windows for.

---

