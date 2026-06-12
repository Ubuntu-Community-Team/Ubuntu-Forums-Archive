---
title: "Wifi not working with Ubuntu installed inside Windows Vista using wubi"
date: 2011-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rohinibc on 2011-05-18
Hi,

I want to know how to get my wireless networks up and running in Ubuntu 11.04 that I recently installed within Vista using wubi. I ve got a Dell 1397 wireless mini card on my Dell Studio laptop.

Any suggestion would be helpful.

Thanks!

---

### Post by garvinrick4 on 2011-05-18
Hook up via ethernet cable to start with.
First thing is to check in additional drivers and enable.

Hit Windows key and "A"  at same time type in additional drivers
and click on to open.

---

### Post by garvinrick4 on 2011-05-18
If a problem: I believe your are 4312 driver.
I it is in here open synaptics if you do need to install:
bcmwl-kernel-source
and
b43-fwcutter

I believe those are the 2:
right click to install then hit apply:
might have to reboot.

Now make sure enabled in additional drivers after installing:
click on thumbnail where you should go.

---

### Post by rohinibc on 2011-05-22
@garvinrick4 - Thanks for posting in. I hooked up a LAN cable and still unable to connect to the Internet. I am not really sure how to proceed. Do I have to configure something after I connect the ethernet to get my internet up and working?

---

### Post by garvinrick4 on 2011-05-23
> **rohinibc said:**
> @garvinrick4 - Thanks for posting in. I hooked up a LAN cable and still unable to connect to the Internet. I am not really sure how to proceed. Do I have to configure something after I connect the ethernet to get my internet up and working?
In your router choose your Name you give to your internet (SSID)  and choose a password
Wired:
MTU is automatic
Method is DHCP
IPv6 is Ignore

Wireless
Pick your SSID and password
Mode is infrastructure
Security is going to be WPA personal (newer)
Some routers have WEP

If you install router and let it pick up the signals from your internet service provider
Will set most all up itself and so does Network Manager in Ubuntu. You have to
give it your SSID and password you set in router and you can check mark the "attach always" in edit network connections in wireless of Network manager (right click on network manager.) 
If you right click on network manager applet check connection information to see if
driver, speed and IP address is all there. (and make sure boxes checked "enable networking "enable wireless")
Run these three in terminal to stop and restart Network Manager. (like a internet reboot)
copy and paste one at a time.
```
sudo service network-manager stop
``````
sudo rm /var/lib/NetworkManager/NetworkManager.state
``````
sudo service network-manager start
```Now below all cards and drivers you can run:
```
lscpi -k
```Above look at your 2 internet cards and see what drivers say:
```
iwlist scan
```above will tell your SSID name and if working for wifi.
```
sudo ifconfig wlan0 up
```above maybe start your wifi.

```
gedit /var/lib/NetworkManager/NetworkManager.state
```This above should all say true.

Most of cards the driver is already in Linux kernel some you have to install
from within Synaptic Package Manager. Or look in additional drivers and enable.
Some versions was called hardware drivers in System/Administration/
There are thousands and thousands that have your same cards so it is just the
matter of finding the driver you need and installing it in Synaptics package manager. Ask in these forums
or  Google it and use your driver name and card and Ubuntu in Google and will
usually get you a how to.
Below will show your internet eth0 (wired) and wlan0(wireless)
```
 ifconfig
```## Dells have a lot of Broadcom cards just type in bcm in Synaptics package manager and will get you there.
In Windows Dell gives you a Windows install DVD's and another disk with their drivers on it. They seperate them from Windows I guess
so if you get to far away from Dell they can smack you on the knuckles. Why seperate disks with drivers? Just a personal opinion, no more than that.

---

