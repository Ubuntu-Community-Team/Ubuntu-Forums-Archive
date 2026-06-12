---
title: "Retail Plus Wireless N usb adapter"
date: 2009-02-21
forum: General Help
---

### Post by StarThorn1 on 2009-02-21
Hi,

I just bought a Retail Plus Wireless N usb adapter. The sales people said they didn't know if it would work for linux or not. I brought it home and pluged it in. I put the driver CD in but linux gave me an error about auto run. 

Does anyone know how I can get this working/ how I can find a linux driver for this? I dont know a whole lot about linux.

---

### Post by dorkdork777 on 2009-02-21
Could you find out the brand and model please?

---

### Post by StarThorn1 on 2009-02-21
Model WL-6200c
and the brand is RetailPlus+
[http://www.retailplus.com/retailplusproducts.htm](http://www.retailplus.com/retailplusproducts.htm)

---

### Post by StarThorn1 on 2009-02-22
bump

---

### Post by Kevbert on 2009-02-22
With the USB adapter plugged in go to Applications-Accessories-Terminal and enter
```
lsusb
```
to list all usb devices and
```
iwconfig
```
to display configuration settings. Please post the outputs of each command here. The alternative is if you have .inf and .sys Windows _XP_ drivers on the CD you can install these instead by installing ndiswrapper and ndisgtk from the installation CD. What version of Ubuntu/Kubuntu/Xubuntu are you using ?

---

### Post by StarThorn1 on 2009-02-22
I am using version 8.10

I found 2 files on the CD 

net8192u.inf and rtl8192u.sys

I installed Ndisgt, went to system>Admin>windows wireless drivers.

The program opened. I clicked INstall new driver and picked net8192u.inf. on the right side it says Net 8192u Hardware present: no. I have it plugged in though

---

### Post by StarThorn1 on 2009-02-22
> **StarThorn1 said:**
> I am using version 8.10

I found 2 files on the CD 

net8192u.inf and rtl8192u.sys

I installed Ndisgt, went to system>Admin>windows wireless drivers.

The program opened. I clicked INstall new driver and picked net8192u.inf. on the right side it says Net 8192u Hardware present: no. I have it plugged in though

ok I figured it all out. My front usb must not give power but my back does. Its wirelss N and I have a wireless N router. How can I tell if im getting above 54.MB ?

---

### Post by Kevbert on 2009-02-22
Well done. You probably won't be able to prove that you're getting above 54Mbs as this is determined by a large number of things. What are you connecting the wireless to ? If the router/source is 54Mbs it does not mean that you'll necessarily see this as it may be limited by your service provider, the web site(s) that you are using, interference etc. If you have a second PC that uses type 802.11n wireless you could try sending a large file (say 1Gb) between the 2 PCs and monitor that for speed.
Take a look at [[COLOR="Red"]this[/COLOR]]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") for setting up adhoc connections.

---

### Post by StarThorn1 on 2009-02-22
Im have a few choices in front of me. I have a second router now in my bed room. I can cut into the wall and lay the wires so they are not running across the floor.

I have wireless N/B/G coming from a Wireless N router. I use it right now with my ps3 to stream videos with Tversity. When I play games online with it though, it keeps signing me out because it loses connection. I don't have many problems streaming the video (Just once, it would pause and catch up every 10 mins)

I only have cat5 right now. Id rather have Cat5E if I'm streaming video. I might be over thinking it and maybe the free cat5 cables I have are good enough.

what do you think?

PS thanks for your help! I had no idea those programs you told me about existed. I looked them up when you told me about it.

---

### Post by Kevbert on 2009-02-22
If you have 802.11n on two computers, the best way to check would be by wireless rather than fixed wire and both within line of sight of each other. If the signal needs to be boosted you can get wireless antenna extensions which will improve the signal a lot (I'm using one as the router is in a different room from two of my PCs and my Wii console and without it I would only just be able to connect to the web). If you decide to go down the wired route cat 5e cable should be fine.

---

### Post by thornspear on 2009-08-16
I have the same wireless usb device.  I'm running ubuntu 9.04.  I have the installation cd, but for some reason ubuntu isn't recognizing it.  I found the net8192u.inf file online though.  I've installed ndiswrapper, when I try and open the .inf file with it I'm getting an invalid driver error.  Is there anything I have to do with the .sys file? 

lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

The usb device is plugged in, but the light on it is extinguished.  

I'm new to linux and the forum, any help would be much appreciated. 

Thanks!

---

### Post by thornspear on 2009-08-16
The wireless usb device is showing as: 

Bus 003 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. 

so ubuntu is recognizing it.

---

### Post by thornspear on 2009-08-17
I've received the following advice on another forum: 

For recent Ubuntu distributions, you don't use the ndiswrapper driver. You will, however, need to find and install the firmware on the system so the builtin driver(s) can use the device.



Anyone know how I would go about doing this?

---

### Post by blahblah1234 on 2009-10-30
Someone pls help! I am at my wits end here :x.  I am trying to get my realtek RTL8192U usb wireless N adapter to work under ubuntu 9.10 but am having some huge problems.  I followed the steps that everyone seems to suggest which was to install ndiswrapper  and ndisgtk. then installed the windows xp drivers as instructed and everything seemed to go fine.  I can see the available networks and signal strength and the light comes on my usb adapter and all looks well.  EXCEPT I CANNOT CONNECT!!  I click on the network to connect get the window that pops up asking for wep 40/128 key, wep 128 pass phrase key, etc.  So i Imput my key and wait and wait and wait some more but no connet, but only get the same window to pop up again a few moments later and this is nothing but one huge long vishes cycle.

---

### Post by thornspear on 2010-10-05
Super late answer but in case anyone else is having this issue; I had my problem solved here: 

[http://www.linuxforums.org/forum/ubuntu-linux/151540-solved-retail-plus-wireless-n-usb-adapter.html](http://www.linuxforums.org/forum/ubuntu-linux/151540-solved-retail-plus-wireless-n-usb-adapter.html)

---

