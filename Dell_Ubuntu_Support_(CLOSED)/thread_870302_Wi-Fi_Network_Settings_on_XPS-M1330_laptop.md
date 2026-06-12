---
title: "Wi-Fi Network Settings on XPS-M1330 laptop"
date: 2008-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-07-25
My M1330 laptop has the BCM4312 chip, and the Bluetooth works fine under Ubuntu 7.10, but I can't get the Wi-Fi to work with my Linksys g-speed router without 1/2 hour of twiddling, tweaking, fiddling, and adjustment in Network Settings.  And when I get it working, the slightest change or restart requires another 1/2 hour of ttfa in the Network Settings dialog.  Could someone please tell me what needs to be entered in that dialog so I can cut down the no. of variable to tweak?

(The following assumes that the Wireless slide button on the side of the laptop is set to "1", i.e. Enable Wireless.)

1)  WPA2 - The wireless card _seems_ not capable of doing WPA2, spontaneously re-setting itself to WPA.  Every time I try WPA2 as a parameter, the Wi-Fi stops working, although the Linksys router is using WPA2, and WPA2 works fine on the Vista-half of my dual-booted system.  Whenever I get Wi-Fi to work, WPA must be in use.  Is there a simple configuration change in Linux that enables WPA2?

2)  Configuration - It's unclear whether the Configuration setting should be "Automatic configuration (DHCP)" or "Static IP address".  One seems to work one time, then the other at another time.  Should both settings work (assuming the static IP addresses are correct)?

3)  Gateway - If the "Static IP address" setting is used for Configuration, what should the Gateway setting be?  I have been using the IP address of the Linksys router (192.168.1.1), but that works sometimes, and not at other times.

4)  Hosts - Does another entry have to added to Hosts?  Once, when I added the address of the router (192.168.1.1), the Wi-Fi worked, but it seems to not require it at other times.

5)  Location - At startup, should it only be necessary to set the Location entry in Network Settings and then to click the checkmark icon to start the Wi-Fi connection?  Or must click Wireless Connection and Propeties and then re-enter all the settings again?


Thanks for any help with these 5 points.  Until I get this resolved, Wi-Fi under Ubuntu on my laptop is tedious, unreliable, and a voracious time-hole.

*TimDaniels*

---

### Post by TimDaniels on 2008-07-28
> **TimDaniels said:**
> My M1330 laptop has the BCM4312 chip, and the Bluetooth works fine under Ubuntu 7.10, but I can't get the Wi-Fi to work with my Linksys g-speed router without 1/2 hour of twiddling, tweaking, fiddling, and adjustment in Network Settings.  And when I get it working, the slightest change or restart requires another 1/2 hour of ttfa in the Network Settings dialog....

A re-installation of Ubuntu 7.10 took care of it.  The only things that I did differently were to turn off all indexing on the theory that indexing was responsible for the increased slowdown of loading (which finally took about a minute to just open Firefox), and not to try loading Adobe Flash or Shockwave.  Now, with wireless networking set to Roaming or Static IP Address, I can connect through the Linksys wireless router.

*TimDaniels*

---

