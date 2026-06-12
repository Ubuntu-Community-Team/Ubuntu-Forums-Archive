---
title: "Wireless problems under KDE 4.2"
date: 2009-03-07
forum: General Help
---

### Post by ahounsome on 2009-03-07
Hi guys, can anyone help with an issue with getting the built in wireless on a Lenovo R60 to work with KDE 4.2? The machine was working perfectly ok under XP so I don't think its a hardware fault and the wireless is set in the BIOS ok. It also works fine with an ethernet cable to the router. The icon in the system tray is green (which I presume is good) and says "Device wlan0 state unmanaged" I was wondering whether I could get the latest wireless driver from the Lenovo site? Any ideas anyone?

---

### Post by abyrne on 2009-03-07
I'm taking a total shot in the dark here.

 But I think Kubuntu should of recognized the wireless card right away and suggested a driver. 

And about that wlan0 unmanaged thing: 
gDon't judge me here but I used to get that messge when I switched my wifi card into moniter mode when I used it to crack WEP WiFi networks.
;)

---

### Post by avtolle on 2009-03-07
What wireless card does your computer have? From the command line (Applications>Accessories>Terminal) please do```
lspci
```and post the results.

EDIT: From Google, it appears that the "stock" Lenovo R60 comes with an Intel wireless card, which should be recognized and work "out of the box", so I'm not sure this is a driver problem.

---

### Post by utnubuuser on 2009-03-07
Something related to:> Go to CentOS page and install the RPMForge plugin.
yum install dkms-ipw3945
lsmod |grep ipw

Done..the wireless card is detected but still cant seem to get the wireless network. After some more digging, found that the ipw3945 project has been deprecated and superseded by Iwlwifi at [http://intellinuxwireless.org](http://intellinuxwireless.org)

Below are notes to try, but I have yet to find the apps that is talk to the wifi daemon that connects to the wireless network.

The ATRpms repository contains Iwlwifi. Plugin to the wired network. Edit the repo file with
[atrpms]
name=EL $releasever - $basearch - ATrpms
baseurl=http://dl.atrpms.net/el$releasever-$basearch/atrpms/stable
gpgkey=http://ATrpms.net/RPM-GPG-KEY.atrpms
gpgcheck=1
enabled=1
exclude=*kmdl*i586*
includepkgs=*iwlwifi* *mac80211*

Since gpgcheck is enabled, run the command
rpm --import [http://ATrpms.net/RPM-GPG-KEY.atrpms](http://ATrpms.net/RPM-GPG-KEY.atrpms)

Install the drivers
yum install iwlwifi iwlwifi-kmdl-`uname -r` 

Look for the iwlwifi driver?

what's the output of > iwconfig say?

---

### Post by avtolle on 2009-03-07
Another question: is your wireless network encrypted? If so, try removing the encryption and see if you can connect in the open.

---

### Post by avtolle on 2009-03-07
And, to further muddy the waters, does this [http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled") apply to your situation at all?

EDIT: Oops, meant [http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945). Sorry.

---

### Post by ahounsome on 2009-03-07
Hi, the chipset is Intel. The wireless controller is - 

"Network controller: Intel Corporation PRO/wireless 3945ABG [Golan] network connection (rev 02)"

Hope this helps

---

### Post by ahounsome on 2009-03-07
Hi again, I've done the iwconfig and got some interesting results. What I failed to mention is that in a old ubuntu forums post I found a manual config setting for lan config and copied in my sky connection details. The iwconfig output is -

"lo no wireless extensions
eth0 no wireless extensions
vmaster0 no wireless extensions
wlan0 IEEE 802.11abg ESSID: SKY*****
Mode: Managed Frequency: 2.462GHz Access point: Not-Associated

pan0 no wireless extensions"

Any good?

---

### Post by ahounsome on 2009-03-08
Ok, well I've got some sort of a result. I loaded up the KDE 4.2 distro on my lenovo T60 and wireless works fine straight out of the box with no problem. It's got to be the wireless chip on the R60 that's knackered. Thanks to all for your help

---

