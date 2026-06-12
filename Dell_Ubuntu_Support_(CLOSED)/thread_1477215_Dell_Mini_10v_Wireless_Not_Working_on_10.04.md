---
title: "Dell Mini 10v Wireless Not Working on 10.04"
date: 2010-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by delirium85 on 2010-05-08
Okay...Just updated to 10.04 on my Dell Mini 10v, and now my wireless is not working.  I do not have access to Ethernet networks where I am at, only wireless.  Is there anyway for me to get the Dell Wireless WLAN card working on 10.04?  Please help!

---

### Post by ugm6hr on 2010-05-08
Yes - as long as you can download some files on to a USB stick (or similar).

Bear with me - I am doing this from memory - I did it a few weeks ago following a new 10.04 install on my Mini 9 (with the same wifi card - I believe).

You can check if you have the same card:
```
lspci
```

You should see in the list:
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

This explains the problem:
[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

If so - you should grab the file from any of the listed sources:
[http://packages.ubuntu.com/lucid/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/lucid/i386/bcmwl-kernel-source/download)

Also - get the firmware files from:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Assuming you have all 3 of these files stored on a USB stick which mounts at /media/disk/
```
sudo dpkg -i /media/disk/bcmwl-kernel-source
```
Then press TAB key to finish the name of the file and then Enter
Follow instructions - and select yes when asked if you want to connect and download files etc.  This will obviously not work - don't worry - just ignore the error messages (although it would be helpful for someone to post what the messages are here).

You need to modify the file which downloads the firmware:
```
gksudo gedit usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

Edit it (lines 7 & 8 changed from wget from web to cp from USB) to look like the following:
```
#!/bin/sh

set -e

dir=$(mktemp -d)
cd "$dir"
cp /media/disk/bcmwl/wl_apsta-3.130.20.0.o "$dir"
cp /media/disk/bcmwl/broadcom-wl-4.150.10.5.tar.bz2 "$dir"
b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
rm -rf "$dir"
chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

```

Then try again:
```
sudo dpkg --configure -a
```

Hopefully, that should now work.  Just follow the instructions, answering Yes again when offered a download.

---

### Post by tygreen101 on 2010-05-11
I also have a Dell mini 10V.  thank you for the help.  It did allow me to connect to my router once, but then after I patched and rebooted, it won't connect again.  Any ideas?

I appreciate all the help.

---

### Post by shiningkenmonster on 2010-05-11
i have a dell mini 10v too. I used to have a router and the internet with an ethernet port. back than, i plugged in the ethernet port upon a fresh install of Ubuntu and went to tab of Systems -> Administrator -> Hardware Drivers. and installed the STA Broadcom drivers. and reboot. and the wifi card would work.

now I don't have the internet connection at home at all. the easiest way for me, was to go to a friend's house and use his ethernet port/internet and install my STA Broadcom drivers. Its the easiest way to to get my wifi working.

---

### Post by ugm6hr on 2010-05-12
> **tygreen101 said:**
> I also have a Dell mini 10V.  thank you for the help.  It did allow me to connect to my router once, but then after I patched and rebooted, it won't connect again.  Any ideas?

I appreciate all the help.

Not sure - make sure after you get connected, that you update everything appropriately, before you get disconnected again.
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

---

### Post by delirium85 on 2010-05-12
I will copy this all to a text document and give it a try tonight.  Thank you so much for the help, and i'll let you know if it works out for me.  Thank you so much, Ubuntu may be saved on my netbook yet.

---

### Post by Felipe Butcher on 2010-06-23
Hi there. Not sure if helps but just to let you know.

I had the very same problem on my vostro and I have the same broadcom card. The solution I found was simple. I just connected the computer to a cable and did an update just like ugm6hr said and everything worked fine.

---

