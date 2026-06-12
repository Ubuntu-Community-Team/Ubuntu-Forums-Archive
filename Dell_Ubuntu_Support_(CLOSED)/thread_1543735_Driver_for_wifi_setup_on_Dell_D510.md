---
title: "Driver for wifi setup on Dell D510"
date: 2010-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mpdsr on 2010-08-01
It all started reading about partitioning my hard drive to be ready for an ubuntu install. Next thing I know I corrupted my hard drive and had to start at the beginning. Enough of my sad tale of woe. I now have both XP and Ubuntu living on my hard drive in complete harmony...except I have no wireless internet on the Ubuntu side. The wifi light is lit but there is no one home! Is there a driver for Ubuntu that will work with my Broadcom 1370wlan mini pci card? And if there is...where do I find it and how do I install it?
Help
MPDSR

---

### Post by pytheas22 on 2010-08-01
All internal Broadcom wireless cards are fully supported on Linux, so you shouldn't have much trouble getting yours running.  My guess is that you're just missing firmware, but please open a terminal and post the output of these commands so we can check exactly what's wrong:
```

lshw -C Network
lspci -nn
dmesg | grep -e wlan -e b43 -e wl
uname -rm
sudo iwlist scan
```

---

### Post by Joe of loath on 2010-08-01
```
sudo apt-get install bcmwl-kernel-source b43-fwcutter bcmwl-modaliases
```

---

### Post by mpdsr on 2010-08-01
mpdsr@mpdsr-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:f2:93:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:18 memory:dfdf8000-dfdf9fff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfdfa000-dfdfbfff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:e7:a0:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
mpdsr@mpdsr-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments Device [104c:8037]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
mpdsr@mpdsr-laptop:~$ dmesg | grep -e wlan -e b43 -e wl
[    1.341680] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.300683] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   15.477009] Registered led device: b43-phy0::tx
[   15.477028] Registered led device: b43-phy0::rx
[   15.477047] Registered led device: b43-phy0::radio
[   15.805529] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   15.827989] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   15.833054] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   15.833135] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.833212] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   15.896057] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   15.901074] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   15.906630] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   15.906714] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.906792] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   41.504048] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   41.518041] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   41.539090] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   41.539097] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   41.539100] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
mpdsr@mpdsr-laptop:~$ uname -rm
2.6.32-21-generic i686
mpdsr@mpdsr-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

Hope I got it all.
Mike

---

### Post by mpdsr on 2010-08-01
Thank you Joe, but:
mpdsr@mpdsr-laptop:~$ sudo apt-get install bcmwl-kernel-source b43-fwcutter bcmwl-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source

---

### Post by mpdsr on 2010-08-01
Guys, I am writing to let you know that after I learned that I could access the web wired I was able to download the updates and the wonderful  system> administration>search for hardware drivers found the proper driver and installed it. Upon reboot and change of security setup I am sending my reply via wifi. Thank you for your prompt assistance. I am sure there will be many other befuddling things that will occur as I begin to learn the workings of Linux/Ubuntu.
Thanks again.
Mike

---

### Post by Guitar John on 2010-08-01
It seems convoluted to me that you need an internet connection to get a working internet connection, but I had to do pretty much the [same thing]("http://dadgadjohn.blogspot.com/2010/05/ubuntu-1004-lts.html") with my Dell D610's to get the wireless working.

Glad to see you got things sorted out.

BTW, Welcome.

---

### Post by pytheas22 on 2010-08-01
Yeah, you just needed firmware.  Ubuntu can't ship what you needed because it doesn't legally have the right to redistribute the firmware and Broadcom won't grant it.  As a result, the only way t get it is to use a wired connection to download it.

The b43 developers are supposed to be working on a reverse-engineered open-source firmware that Ubuntu could ship legally, but I'm not sure when that will be used (I think Fedora already uses it but it may not work well).

Anyway, glad you figured it out and hope you enjoy Ubuntu.

---

### Post by mpdsr on 2010-08-03
Well Ubuntu lasted a day. I got started using it and enjoying some of it's perks and even spent the big money to buy a book or two on Unix and Ubuntu, however after updating the system it began to act funny. (A real descriptive use of computer language). When I rebooted there was an error message stating that there was a Gnome error and for me to contact my system administrator. Uhhh. I take it that is me...and I don't have a clue. Is it possible I downloaded an update for a different version of Ubuntu and it ruined my 10.04? I don't speak Unix and so I am at a loss. Is it gnome or is it G-nome? I don't even know how to say it. Any suggestions? When I put the boot disk back in it took me to a terminal and after logging in it sat there awaiting input happily blinking at me.
Mike

---

### Post by pytheas22 on 2010-08-03
If you copy the exact error message here, we may be able to help you figure out what's wrong.  It's possible you got a bad update, or something else went awry when you were playing with the new system.  Problems with Gnome are usually not actually that bad; chances are you just need to adjust some file permissions or something like that.

You could also of course always just reinstall from scratch.  I went through about a dozen reinstalls over the course of several months when I first started using Linux before I finally got it straight.  The problem wasn't Linux itself as much as my inability to resist the temptation to screw around with things, and reinstalling was the only way I knew to fix the system after my tinkering inevitably broke it.  I've since learned that it can almost always be fixed without a reinstallation, but it took awhile to get to that point!

As for how to say Gnome, I don't think anyone knows :)  I say Nome, but I've heard G-Nome often enough as well.  I've also seen it spelled alternately as GNOME and Gnome by the developers themselves, so that's always confused me too.

---

### Post by mpdsr on 2010-08-12
I did the re-install and all is well. Other than not being able to get my Sony Reader to function (Adobe Digital Editions has no Linux/Ubuntu drivers) I have come to like Ubuntu and have just kicked XP to the curb on my Inspiron 1501. I have kept XP on the Latitude to be able to get my ebooks, etc, but will eventually abandon it when I have all the drivers I need for my Home Recording software. I have been reading up on Ubuntu and hopefully will get a handle on it in a reasonable amount of time.
Thanks for your input. I really appreciate it. All I read about the strength of Ubuntu being it's community appears to be accurate.
MPDSr:)

---

### Post by mike9682000 on 2010-08-31
Hello all,

I have the exact same problem, EXCEPT that I cannot connect the laptop to the internet. I can, however, connect to the internet using another computer (running windows XP).

As an absolute newbie, how do I download the driver into a stick, then install it on my laptop?

Thx,
Mike

---

### Post by pytheas22 on 2010-09-01
> I have the exact same problem, EXCEPT that I cannot connect the laptop to the internet. I can, however, connect to the internet using another computer (running windows XP).

As an absolute newbie, how do I download the driver into a stick, then install it on my laptop?

I can give you instructions for getting the files you need without having an Internet connection, but first please post the output of the following commands so we'll know exactly which type of wireless card you have (even if your computer model is the same as other posters' in this thread, the wireless chipset could be different):
```

lspci -nn
lsusb
lshw -C Network
uname -rm
cat /etc/issue
```

You can paste the output into a blank text file (open one by going to Applications>Accessories>Text Editor), then transfer that file to your Windows computer using a USB stick so that you can upload its contents here.

---

