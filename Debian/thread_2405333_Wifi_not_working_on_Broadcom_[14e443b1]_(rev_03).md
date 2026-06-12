---
title: "Wifi not working on Broadcom [14e4:43b1] (rev 03)"
date: 2018-11-04
forum: Debian
---

### Post by nasi-n on 2018-11-04
Hi everyone,

Looking for some assistance. The above network device does not work on a fresh install of Ubuntu 18.04.

Apt-get was unable to locate package bcmwl-kernel-source, but as (rev 03) is not an option on the list here [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) I chose to look for help before installing the incorrect drivers.

I have attached a diagnostic report.

Thanks for any and all help in advance.

Regards,
Nasi

---

### Post by chili555 on 2018-11-04
> [  372.036060] ERROR @wl_notify_scan_status : 
[  372.036063] wlp2s0 Scan_results error (-22)
[  425.060075] ERROR @wl_notify_scan_status : 
[  425.060078] wlp2s0 Scan_results error (-22)
[  469.086453] ERROR @wl_dev_intvar_get : 
[  477.728127] ERROR @wl_notify_scan_status : 
[  477.728127] wlp2s0 Scan_results error (-22)
Ouch!!!

Just as an experiment, let's try the other Broadcom driver possibility.

With the ethernet connected and working, open a terminal and do:```
sudo -i
apt install firmware-b43-installer
echo "blacklist wl"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us see a new diagnostics report, please.

---

### Post by nasi-n on 2018-11-05
Thank you, report attached.

---

### Post by chili555 on 2018-11-05
> [    4.254210] b43-phy0: Broadcom 4352 WLAN found (core revision 42)
[    4.254634] b43-phy0 [COLOR="#FF0000"]ERROR: FOUND UNSUPPORTED PHY[/COLOR] (Analog 12, Type 11 (AC), Revision 1)As we suspected. The short explanation is that b43, bcma and firmware are not correct for the device. 

There is one last thing that we might try. Again, with the ethernet connected and working, open a terminal and do:```
sudo nano /etc/modprobe.d/blacklist.conf
```Change this line:```
blacklist wl
```To comment it out, like this:```
#blacklist wl
```Proofread carefully, save and close the text editor.

Now do:```
sudo apt purge bcmwl-kernel-source
sudo apt install broadcom-sta-dkms
```The latter is a slightly newer version. Let's see if it corrects the errors above.

Reboot with the ethernet detached. Run: ```
iwconfig
dmesg | grep wl
```Hook up the ethernet and post the outcome.

---

### Post by nasi-n on 2018-11-06
Thanks chili555,

sudo apt purge bcmwl-kernel-source
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source

```

I should have stopped here considering the package was not removed, so may make the results below irrelevant.

iwconfig
```
lo        no wireless extensions.

enp1s0f0  no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

dmesg | grep wl
```
[    0.000000] DMI: Hewlett-Packard HP EliteBook 745 G2/221C, BIOS M84 Ver. 01.07 03/10/2015
[    4.114250] wl: loading out-of-tree module taints kernel.
[    4.114255] wl: module license 'MIXED/Proprietary' taints kernel.
[    4.159736] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    4.313285] wl 0000:02:00.0 wlo1: renamed from wlan0
[    4.803736] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    4.991770] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  305.473535] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  620.047042] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
```

Thanks again.

---

### Post by chili555 on 2018-11-06
Wierd. 

Let's see: ```
sudo apt update
```You needn't show all the output, just execute the command before you proceed with:```
sudo dpkg -s bcmwl-kernel-source 
sudo dpkg -s broadcom-sta-dkms
```If your wireless does this: > [    4.114250] wl: loading out-of-tree module taints kernel.
[    4.114255] wl: module license 'MIXED/Proprietary' taints kernel.
[    4.159736] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    4.313285] wl 0000:02:00.0 wlo1: renamed from wlan0Then one of the two is loaded.

Please note that in your latest dmesg, the errors I quoted above do not appear.

---

### Post by nasi-n on 2018-11-06
Seems like bmcwl-kernel-source is not installed:
```
dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available

```

...and broadcom-sta-dkms is...
```
Package: broadcom-sta-dkms
Status: install ok installed
Priority: optional
Section: non-free/kernel
Installed-Size: 14140
Maintainer: Eduard Bloch <blade@debian.org>
Architecture: all
Source: broadcom-sta
Version: 6.30.223.271-5
Provides: broadcom-sta-modules
Depends: dkms (>= 2.1.0.0)
Recommends: wireless-tools
Conflicts: broadcom-sta-modules
Conffiles:
 /etc/modprobe.d/broadcom-sta-dkms.conf c5d2490e6167f876e7aae7b4f08e16e6
Description: dkms source for the Broadcom STA Wireless driver
 Broadcom STA is a binary-only device driver to support the following IEEE
 802.11a/b/g/n wireless network cards: BCM4311-, BCM4312-, BCM4313-,
 BCM4321-, BCM4322-, BCM43142-, BCM43224-, BCM43225-, BCM43227-, BCM43228-,
 BCM4331-, BCM4360-, and BCM4352-based hardware.
 .
 This package provides the source code for the wl kernel modules and makes use
 of the DKMS build utility to install them for the running kernel. The
 alternative package broadcom-sta-source can be used instead in case of build
 problems.
 .
 The wireless-tools package is also required in order to make use of these
 modules. Kernel source or headers are required to compile these modules.
Homepage: http://www.broadcom.com/support/802.11/linux_sta.php
root@debian-drogba:/home/sibongilembatha# apt install wireless-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wireless-tools is already the newest version (30~pre9-12+b1).
The following package was automatically installed and is no longer required:
  myspell-sv-se

```

Will appreciate any other suggestions!

---

### Post by chili555 on 2018-11-06
Does it see networks?```
sudo iwlist wlo1 scan
```We needn't see the whole list, just tell us if it sees networks or gives some other error or message.

---

### Post by nasi-n on 2018-11-08
Hi Chili555,

Result of sudo iwlist wlo1 scan:
```
s1o1      No scan results
```

---

### Post by nasi-n on 2018-11-08
Correction:

```
wlo1      No scan results
```

---

### Post by jeremy31 on 2018-11-08
Moved to Debian subforum

---

### Post by chili555 on 2018-11-08
If you walk the laptop right next to the router, are there still no scan results? 

If there are now scan results, we wonder if both antenna wires are connected securely. If there are still no scan results, then, regrettably, I have no other suggestions aside from a new wireless card; eithe PCI or USB.

---

### Post by nasi-n on 2018-11-08
The scan was done about 2m from the router. Strange thing is, the WiFi worked (I removed Windows 8 for Linux) just fine on Windows 8. Both LiveUSB and HDD installs of Debian/Ubuntu did not work, no scan results.

I thank you for your time and effort and wish there was something that could be done to get it working. The laptop was purchased used for an employee to learn about Linux, but I will have to reinstall Windows in order to move forward.

Thanks again.

---

### Post by chili555 on 2018-11-08
It is certainly possible to replace the wireless card in the laptop, barring a whitelist. [https://www.wirelesshack.org/wp-content/uploads/2015/09/How-To-Install-Upgrade-Your-Laptop-to-Wireless-802.11ac.jpg](https://www.wirelesshack.org/wp-content/uploads/2015/09/How-To-Install-Upgrade-Your-Laptop-to-Wireless-802.11ac.jpg)  As well, there are many inexpensive USB wireless devices available: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

In any event, I am sorry I couldn't be more helpful.

---

### Post by nasi-n on 2018-11-08
Thanks, I shouldnt give up so easily. Thanks to your linked thread, the closest USB device locally was this:

[https://www.amazon.com/D-Link-Wireless-Network-Adapter-DWA-131/dp/B002PD61Y4/ref=cm_cr_arp_d_product_top?ie=UTF8](https://www.amazon.com/D-Link-Wireless-Network-Adapter-DWA-131/dp/B002PD61Y4/ref=cm_cr_arp_d_product_top?ie=UTF8)

Will take a chance and see if it works!

---

### Post by chili555 on 2018-11-08
> **nasi-n said:**
> Thanks, I shouldnt give up so easily. Thanks to your linked thread, the closest USB device locally was this:

[https://www.amazon.com/D-Link-Wireless-Network-Adapter-DWA-131/dp/B002PD61Y4/ref=cm_cr_arp_d_product_top?ie=UTF8](https://www.amazon.com/D-Link-Wireless-Network-Adapter-DWA-131/dp/B002PD61Y4/ref=cm_cr_arp_d_product_top?ie=UTF8)

Will take a chance and see if it works!You will need to blacklist the internal Broadcom when you install the USB. Post back if you need additional guidance.

---

### Post by nasi-n on 2018-11-12
USB adapter received. I would really appreciate help in ensuring the internal adapter is blacklisted.

Thanks!

---

### Post by chili555 on 2018-11-12
> **nasi-n said:**
> USB adapter received. I would really appreciate help in ensuring the internal adapter is blacklisted.

Thanks!
From the terminal:

```
sudo -i
modprobe -r wl
echo "blacklist wl"  >>  /etc/modprobe.d/blacklist.conf
exit
```You should be all set.

---

### Post by nasi-n on 2018-11-13
Thank you. Have blacklisted the module successfully, but with the USB adaptor connected, there is no wireless dialogue.

lsusb does show the adaptor as connected.

Any tips?

---

### Post by chili555 on 2018-11-13
Please show us:```
lsusb
iwconfig
```

---

### Post by chili555 on 2018-11-14
Please check post #10 here: [https://ubuntuforums.org/showthread.php?t=2405673&p=13816190#post13816190](https://ubuntuforums.org/showthread.php?t=2405673&p=13816190#post13816190)

---

### Post by nasi-n on 2018-11-14
Hmmm....WiFi working perfectly now! Thanks! Will just keep en eye out for stable connection.

Is there anything that can be done to somehow make such a fix more widely known? I am sure its something that affects a lot of people.

---

### Post by chili555 on 2018-11-14
I just read about it today and was anxious for you to test it for us.

I will pass the word whenever I can.

Glad it's working.

---

