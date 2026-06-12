---
title: "Mouse issue"
date: 2008-10-07
forum: Desktop Environments
---

### Post by imnotorginal on 2008-10-07
Hello all,

I have recently install ubuntu 8.10 on my desktop and instantly feel inlove with it.  I also went ahead and installed compiz as well and feel that the effects that come with this are far better and more stable than those of vista. I fell so much in love with it, that I instantly went the next day and installed it on my laptop.  Both systems are working perfectly fine, except for 1 small problem.  For some reason, after a random amount of time, my mouse will decide to freeze up on my desktop.  I tried getting another mouse to use, but I still got the same results.  I was wondering if anyone has had this happen to them and if so what did they do to correct the issue.  Thank you in advance for any help given.

Andy
Made believer in open source.

BTW if it helps any, both mice I used are USB mice, and 1 was a optical microsoft mouse.

---

### Post by Rotag on 2008-10-07
I'm having the same issue with Ubuntu 8 on my desktop. I have a USB optical mouse. Also, my caps and scroll lock lights flash at lock-up.

---

### Post by caleb12 on 2008-10-08
I just started working with Intrepid this last week... I'm loving it also... 

I just finished getting my mouse all nice and tweaked. From what I understand Xorg 7.4 and xserver 1.5 (Intrepid default) started relying on evdev more than xorg.conf for input device identification. 

There's a couple things you can do to work with this... Firstly, any problems are going to be in your xorg log (/var/log/Xorg.0.log) also, setting up xorg.conf is done a little differently now. For instance my VX Nano entry looks like this: 

Section "InputDevice"
        Identifier      "VX Nano"
        Driver          "evdev"
        Option          "Device"                "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:1d.3-2/input0"
        Option          "Buttons"               "9"
        Option          "WHEELRelativeAxisButtons" "4 5"
        Option          "HWHEELRelativeAxisButtons" "7 6"
        Option          "Protocol"              "evdev"
        Option          "CorePointer"
EndSection

The main problem I was having is that HAL (evdev) was identifying two USB devices, my receiver and the actual mouse. Interestingly it would always identify one as a keyboard device, which then when I logged in would cause my actual keyboard to basically spit out randomness... This issue went away when I added the "Dev Phy" option to the above section, this told evdev which specific device to reference... 

I was able to piece this together from these sources:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware)

[http://mint.gentoo-wiki.com/X11_Mouse/Individual_Configurations](http://mint.gentoo-wiki.com/X11_Mouse/Individual_Configurations)

Also there are a couple options in the ServerLayout section that allows you to disregard any input from evdev (hal). But, now everything seems to be working very well... all my buttons are functional and I have been able to map them into compiz without an issue.

---

### Post by shokoup on 2008-10-08
I have the same problem after Compiz, with micosoft serial mouse

---

