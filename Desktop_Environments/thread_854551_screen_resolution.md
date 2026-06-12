---
title: "screen resolution"
date: 2008-07-09
forum: Desktop Environments
---

### Post by Caveageman on 2008-07-09
just installed Ubuntu hardy on to a laptop and only one of the screen resolutions works. and i can only see the top corner of the desktop. all the other resolutions just give me fuzz. can any one help me?

---

### Post by atomkarinca on 2008-07-09
Hit alt+F2 and type "displayconfig-gtk" (without the quotes), select your monitor and then your correct resolution. If you have an Nvidia card then again and type "gksudo nvidia-settings" (again without the quotes) and hit "Save to X Configuration File", restart and you should be OK.

---

### Post by Caveageman on 2008-07-09
Thank you but i dont know if i have a nvidia card and that second conmand doesnt do anything just back to the command line and the first one goes to a window thing i can select a resolution and click test its fine click ok and nothing happens just dissapears back to the desktop. thanks again

---

### Post by atomkarinca on 2008-07-09
You should log out and log back in for changes to take effect.

---

### Post by Caveageman on 2008-07-09
i have rebooted will just try logging out and in

---

### Post by Caveageman on 2008-07-09
still no effect : (

---

### Post by adieb on 2008-07-09
i think you should find out what graphic card you are using by typing
```
lspci
```
in terminal.

If you have problems to open a terminal, just switch away from your x-environment by typing
```
Strg-Alt-F2
```
then log in.

the result should look like:
```
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

you can see it says "VGA compatible controller: nVidia Corporation GeForce 8400 GS", look for something similar.

Or post your result here

---

### Post by Caveageman on 2008-07-09
```

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```
its says via alot?

---

### Post by adieb on 2008-07-09
Hey,

i think in this thread you´re going to find the solution for your resolution ;-)

[URL="http://forum.ubuntuusers.de/topic/165210/?p=1336088#1336088"]

good luck!

EDIT:
Oh, sorry, i didn´t realize it is in german language...
you don´t understand german? do you?

---

### Post by adieb on 2008-07-09
so here a possible solution in english:


remove unwanted drivers:
```
sudo apt-get -f remove xserver-xorg-video-openchrome xserver-xorg-video-unichrome
```


edit your xserver-config:
```
sudo gedit /etc/X11/xorg.conf
```

go to section "device" an change Driver "vesa" to Driver "via" + add two lines. it should look like this:
```
Section "Device"
   Identifier "VIA Technologies"
   Driver "via"
   BusID "PCI:1:0:0"
   Option "VBEModes" "true"
   Option "EnableAGPDMA"
EndSection
```

Save the file and restart your X-Server by:
```
Strg-Alt-Backspace
```

to check if your driver is working  type:
```
glxinfo | grep direct
```

when it says "Direct rendering = yes" it worked

---

