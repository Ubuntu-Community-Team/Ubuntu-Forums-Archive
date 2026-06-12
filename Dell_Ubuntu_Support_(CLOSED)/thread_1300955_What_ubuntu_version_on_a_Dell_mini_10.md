---
title: "What ubuntu version on a Dell mini 10?"
date: 2009-10-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by erick_king on 2009-10-25
I have a new Dell Inspiron mini 10. It had Windows and the resolution screen was acceptable. But I dont use windows since one year ago. And I dont want to use it anymore. At my school I installed on all machine ubuntu 9.04 and they work very fine. 

But my Dell Mini with ubunto 9.04 or 9.10 doesn't work fine with the resolution screen: i get only 800*560 and really looks bad...

so, my question is: whta is the best version of ubuntu to use in this computer?

I tried already: ubuntu desktop version 9.04, UNR 9.10, and I am thinkin to download the dell version(9.04) 

Thanks in advance!

---

### Post by scout4536 on 2009-10-27
I have been using Ubuntu 9.04 for quite some time now on my Dell Mini 10.  I've got my screen resolution looking great by following this link [http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/](http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/).  My resolution is 1024x600.  I have no problems with freezes or slow video.  Everything seems to be working as planned.  I do hope this helps you out a bit.

---

### Post by scout4536 on 2009-10-27
Oh, and please scroll down to the very end of this link for the best instructions on how to do so posted by Lindylex.

---

### Post by scout4536 on 2009-10-27
1. create the file /etc/apt/sources.list.d/ubuntu-mobile.list
2. sudo vi /etc/apt/sources.list.d/ubuntu-mobile.list
3. add the following content to the newly created file:
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
4. sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys C6598A30
5. sudo apt-get update
6. sudo aptitude install psb-kernel-source psb-kernel-headers
7. sudo reboot
8. sudo aptitude install xserver-xorg-video-psb poulsbo-driver-2d poulsbo-driver-3d
9. sudo reboot


“Device” section of /etc/X11/xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Option “AccelMethod” “EXA”
Option “DRI” “off”
Option “MigrationHeuristic” “greedy”
EndSection

I used sudo nano /etc/X11/xorg.conf  to edit the conf file, then once done press ctrl+o and enter to save, then ctrl+x to exit file.

---

### Post by fjgaude on 2009-10-28
My mini 10n came with 8.04 and with a 1388 x 768 screen... what a joy to use! I don't know if I will updage to 9.10, but likely will try when it is released tomorrow. Will try with the LiveCD first, of course. I also have the original install on a USBkey drive, just in case.

---

