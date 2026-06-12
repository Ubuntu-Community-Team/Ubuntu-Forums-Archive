---
title: "Virtual Box machine on UBUNTU - AGAIN"
date: 2009-05-25
forum: General Help
---

### Post by luisridaocruz on 2009-05-25
**Re: Install VIRTUAL MACHINE UBUNTU** 			
 			 			 		   		 		 		LAst week I reported an error while installing
a Virtual Machine. The response was to edit the 
/etc/modprobe.d/blacklist file but as there are several such files under
/etc/modprobe.d/ 

[B]alsa-base.conf           blacklist-framebuffer.conf  dkms.conf
blacklist-ath_pci.conf   blacklist-modem.conf        libpisock9.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-watchdog.conf[/B]

I don't really know which one I should edit.
The response (last week) also stated that I should blacklist kvm in the file.Should I add the following line to such file?

**blacklist kvm**

Best,
Luis

---

### Post by Legace on 2009-05-25
1) Open Terminal and type in the following
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Enter your password and press Enter.

2) Scroll to the end of the text file and add **blacklist kvm**
3) Save the file (CTRL + S)
4) Reboot
5) Now it should work.

---

