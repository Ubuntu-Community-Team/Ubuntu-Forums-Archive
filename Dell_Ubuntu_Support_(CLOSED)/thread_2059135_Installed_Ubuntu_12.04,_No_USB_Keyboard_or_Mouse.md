---
title: "Installed Ubuntu 12.04, No USB Keyboard or Mouse"
date: 2012-09-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bbarton11 on 2012-09-17
Hi All,
 
I installed Ubuntu 12.04 LTS on my new Inspirion 2020 All-In-One as a dual-boot with Win7. At the grub menu I can use the keyboard to make my selection. When I go into Ubuntu, I get the logon screen but I cannot use the keyboard or mouse. It's a wireless keyboard/mouse.
 
Anyone know how to get them to work?
 
Thanks!

---

### Post by bbarton11 on 2012-09-17
Sidebar: The keyboard and mouse worked with no issues from the USB stick that I booted from to perform the install.

---

### Post by Caladus on 2012-09-17
What model/brand USB Keyboard/Mouse? Logitech? And is it the Unifying Receiver or two separate usb wireless dongles?

---

### Post by bbarton11 on 2012-09-17
> **Caladus said:**
> What model/brand USB Keyboard/Mouse? Logitech? And is it the Unifying Receiver or two separate usb wireless dongles?
 
It is the stock wireless keyboard/mouse and USB receiver that comes with the Inspiron 2020. It's Dell.

---

### Post by bbarton11 on 2012-09-18
> **bbarton11 said:**
> It is the stock wireless keyboard/mouse and USB receiver that comes with the Inspiron 2020. It's Dell.
 
The model number is Dell KM632 Wireless Keyboard/Mouse combo.  Thanks!

---

### Post by Caladus on 2012-09-18
Have you tried any other usb devices in the port that your wireless usb is plugged in? Or have you tried moving the USB dongle to another port?

Sometimes there can be signal issues with a rear port on desktops.

---

### Post by bbarton11 on 2012-09-18
Thanks for your reply. Yes I tried other ports with the USB dongle and no luck. I also trIed plugging in a wired keyboard and mouse and same results - no connection.

---

### Post by Caladus on 2012-09-18
Please post the output of these commands :

lsusb

lsmod | grep usb

Thanks!

---

### Post by bbarton11 on 2012-09-19
> **Caladus said:**
> Please post the output of these commands :

lsusb

lsmod | grep usb

Thanks!

lsusb output:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 064e:812b Suyin Corp. 
Bus 002 Device 003: ID 154b:0057 PNY 
Bus 002 Device 004: ID 413c:2501 Dell Computer Corp. 
Bus 002 Device 005: ID 0fcf:1008 Dynastream Innovations, Inc. 
Bus 001 Device 005: ID 0cf3:e004 Atheros Communications, Inc. 

lsmod | grep usb output:
btusb                     18288  2 
bluetooth             180104  24 ath3k,rfcomm,btusb,bnep
usbhid                    47199  0 
hid                           99559  1 usbhid
usb_storage         49198  1

These were from booting my machine from a Live USB stick.  If I boot from the Ubuntu part of the dual-boot, I can't move the mouse or use the keyboard to get output.

Thanks!

---

### Post by bbarton11 on 2012-09-20
bump

---

### Post by bbarton11 on 2012-09-21
I installed Ubuntu 12.10 beta and the wireless keyboard/mouse worked with no problem!  I'm guessing that the newer kernel (3.5 that comes with 12.10) addresses the hardware (12.04 came with kernel v3.2).

---

### Post by bbarton11 on 2012-09-26
Update: I installed Ubuntu 12.10 on my system and the wireless keyboard/mouse work with no issues.  I'm guessing that it's a kernel issue with 12.04.  Is there a way to install 12.04 LTS and then upgrade the kernel before booting into the OS?

---

### Post by bjforesthowell on 2012-11-05
We're experiencing the same thing on these two threads as well....

[http://ubuntuforums.org/showthread.php?p=12337832#post12337832](http://ubuntuforums.org/showthread.php?p=12337832#post12337832)

[http://ubuntuforums.org/showthread.php?p=12337827#post12337827](http://ubuntuforums.org/showthread.php?p=12337827#post12337827)

---

### Post by bjforesthowell on 2012-11-06
I've got an NVIDA vido card and this worked for me after working with NikTh (nick-athens30) on launchpad....

During boot you're going to see a purple screen with no Grub options if you're not dual booting. When you see that purple screen hold the [SHIFT] key until grub menu appears and select "Advanced settings".

At this point, you're going to want to select the kernel with the recovery mode options and just hit enter at the next screen.

Once I was in recovery mode I had my input devices and everything was gravy. I was able to run the software update then, while I was in I installed drivers with the directions from this site...

[http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

Now my global menu and launcher aren't coming up, but this shouldn't be a problem to fix now that I've got input devices.

I hope this helps...

---

### Post by bjforesthowell on 2012-11-07
If you've got an Nvidia video card here's how you get your top menu and launcher back after you have access to your input devices...

[http://askubuntu.com/a/202587/104413](http://askubuntu.com/a/202587/104413)

---

