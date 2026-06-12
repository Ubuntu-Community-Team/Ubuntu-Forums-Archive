---
title: "No internet on Dell Mini 10v with 10.10!"
date: 2010-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PuddingKnife on 2010-10-06
So, my girlfriend asked me to install Ubuntu on her Dell Mini 10v netbook. It is missing "firmware" apparently, and will not connect to the internet even using a wired connection. 

Can anyone help me figure out how to fix this?

EDIT:
Forgot to mention, I ran lspci and got:

> 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

SO... I started following the instructions I found here:

[http://ubuntuforums.org/showthread.php?t=1477215](http://ubuntuforums.org/showthread.php?t=1477215)

When I ran the command 
```
sudo dpkg -i /media/2gig/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
```

I get this error:

> dpkg: dependency problems prevent configuration of bcmwl-kernel-source: 
bcmwl-kernel-source depends on dkms; however: 
Package dkms is not installed.
dpkg: error processing bcmwl-kernel-source (--install): dependency problems - leaving unconfigured
Errors were encountered while processing:
bcmwl-kernel-source

So I haven't followed any more instructions from that thread until I can get this sorted out. You're my only hope, Ubuntu Forums!

---

### Post by PuddingKnife on 2010-10-06
So, I was able to find a DKMS .deb file and successfully installed it, but I am still receiving errors when I attempt to install the bcmwl-kernel-source..

---

### Post by PuddingKnife on 2010-10-07
Gave up on 10.10 and did a fresh install of 10.04. Same exact problems. No connection via ethernet OR wireless. 

This forum is crickets, but I thought I'd let you know anyway.

---

### Post by bastobuntu on 2010-10-13
Hey there!

I've had the same problem than you but luckily my wired and wifi connection is working.

I installed the latest maverick iso from the cd-image server and got wired connection "out of the box"
But since i installed it in a train with no wired internet connection ;) i couldnt update right from the beginning. At home i then installed the Broadcom STA Wifi driver with an error but i works now. The only problem i have now is, that everytime i install something, the installation progress is telling me an error from the wifi card (!!??) but later on the programs are working. Dont ask me why i get an error with the wifi dpkg when installing skype perhaps (which didnt work :( ) but hey - the rest is working very fine!

choose this image. I made a Live-USB with Unetbootin...
[http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/20101007/](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/20101007/)

greets

edit: lspci gives me:
Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by Umkus on 2010-10-13
Confirmed. I installed Maverick 10.10 just yesterday on my Dell mini 10v, with wired network broken. Wireless works ok, though.
Anybody else have this problem?
I will be trying to start from live usb using another distributions and recheck.

Since just before I installed the Ubuntu and my Mac OS installation was still in one piece, I was able to use wired/wireless network there. Now only wireless works in Maverick. So it is definitely not a hardware issue.

lspci:
> 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

ifconfig -a:
> eth0      Link encap:Ethernet  HWaddr 00:24:e8:c8:2c:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1936 (1.9 KB)  TX bytes:5291 (5.2 KB)
          Interrupt:43 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:39:b7:93  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe39:b793/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25493 errors:0 dropped:0 overruns:0 frame:4031
          TX packets:7332 errors:65 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19885550 (19.8 MB)  TX bytes:587500 (587.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3312 (3.3 KB)  TX bytes:3312 (3.3 KB)


---

### Post by Denton Larson on 2010-10-13
Hi

Check out this web site, I have a dell mini 10 and it worked for me.

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Denton

---

### Post by Umkus on 2010-10-13
> **Denton Larson said:**
> Hi

Check out this web site, I have a dell mini 10 and it worked for me.

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Denton

Thanks, but no. That's fixing wireless problems. Wireless networking is working nicely for me. Wired(Ethernet) doesn't. That's what strange.

I read a guy said pulling off battery and holding the Power button for 15 seconds should bring Ethernet back to life, but it didn't in my case.

---

### Post by jazmanjal on 2010-10-13
same with me just now, happen when I load 10.10 to my gf Dell Mini. 10.04 before I'm using ndisgtk to use windows xp driver but unfortunately it not works today. 
Alternatively I update Broadcom Wireless driver kernel with this command
sudo apt-get update 
sudo apt-get install bcmwl-kernel-source

then I reboot, and it works! :)

---

