---
title: "Help with USB Wireless ZyDAS"
date: 2005-12-23
forum: Desktop Environments
---

### Post by Georgie-o on 2005-12-23
My USB Wireless doesn't seem to working.  Tried various things but I'm a newb.  Testing Dapper "Live" on my laptop as the 5.10 would not work.  Great news is Dapper works nicely.  Bad news, can't figure out wireless.  I downloaded a driver (the file is unpacked and sitting on my desktop called "zd1211-4916").  Do I just stick that somewhere?  Where?  Anyhelp would be appreciated.  Here is a print out that I made re: whats installed:

ubuntu@ubuntu:~$ sudo lshw -C generic
  *-usb
       description: Generic USB device
       product: USB2.0 WLAN
       vendor: ZyDAS
       physical id: 2
       bus info: usb@1:2
       version: 48.10
       capabilities: usb-2.00
       configuration: driver=zd1211 maxpower=500mA speed=480.0MB/s
ubuntu@ubuntu:~$

---

### Post by Lambert on 2005-12-25
>         configuration: driver=zd1211

You shouldn't have to do anything as the above line in the output shows a driver is allocated to the device. (zd1211 is a module/driver that comes with ubuntu so no driver needs to be added)

All you should have to do is go into system>administration>networking and set the properties and activate. If the device is not in the list then there is a problem at the driver level. 

Are you running wep or wpa? if so there are some other things that (might)need to happen to make it

---

### Post by Georgie-o on 2005-12-31
The USB device does not show up under netwroking.  How do I make it find it?

thanks

---

### Post by Georgie-o on 2005-12-31
I tried all the things I could figure on the like you provided above.  It appears that Ubuntu has the correct driver and the it picks up the USB device, but no luck getting it to show up under Networking.  Any thoughts would greatly appreciated.
This is the output from the commands porvided:


george@ubuntulaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

george@ubuntulaptop:~$ lsusb
Bus 003 Device 002: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 001 Device 001: ID 0000:0000
george@ubuntulaptop:~$ sudo modprobe zd1211
george@ubuntulaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

george@ubuntulaptop:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
george@ubuntulaptop:~$

---

### Post by Lambert on 2005-12-31
According to this post zd1211 that comes with breezy doesn't work. so follow his instructions on installing from source.

[http://www.ubuntuforums.org/showthread.php?t=92327&highlight=zydas](http://www.ubuntuforums.org/showthread.php?t=92327&highlight=zydas)

---

### Post by Georgie-o on 2005-12-31
I tried the steps but failed to properly complete.  The fix is over my level of skill at this point.  Is it reasonable to expect that the final, or future pre-releases of Dapper will include a fix that has working ZyDAS 1211 and that it will automatically find the USB wireless?

---

