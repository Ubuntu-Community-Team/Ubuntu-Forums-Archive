---
title: "Unable to change the monitor resolution"
date: 2010-03-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Anton90125 on 2010-03-08
Hello,

I am a newbie to Linux and thought I would get Ubuntu to learn about this OS. I got a second hand PC from Ebay a DELL GX280 P4 2.8GHZ. I set this up as a duel boot and successfully installed Ubunto 9.10.

Everything seems to be ok except the monitor (IIyama HM903DTA Vision Master Pro 454) resolution seems to be restricted to 800 x 600 (60 Hz) and 640 x 480 (60 Hz). I know that the monitor can go higher as I use it with windows 1024 x 768 (85 Hz).

When i try System>Preference>display I get unknown monitor.

I have these bits of infomation:

 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL  Integrated Graphics Controller (rev 04)

anton@anton-Linux-desktop:~$ lspci
00:00.0 Host bridge: Intel  Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0  PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root  Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation  82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1  Display controller: Intel Corporation 82915G Integrated Graphics  Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation  82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1  PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI  Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation  82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB  Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
00:1d.2 USB  Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation  82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB  Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2  EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801  PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel  Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller  (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR  (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface:  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller  (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW  (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel  Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev  03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme  BCM5751 Gigabit  Ethernet PCI Express (rev 01)
anton@anton-Linux-desktop:~$ 

When I typed gksudo gedit /etc/X11/xorg.conf in the terminal I get an empty file. There are no details.

How can I get ubuntu to display at a higher resolution? Any help would be of great value.

Thanks

Anton

---

### Post by Tikkyca on 2010-03-08
You need to install driver for your graphic card you can do that using update menager,you can change resolution from there if that doesn't work you can find some other dislpay menagers,they will detect your monitor(i hope so).

---

### Post by realzippy on 2010-03-08
You could try a standart setting for intel.
Copy this:

[I]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/I]

into your empty xorg.conf file,restart.
If you -do not think so- cannot start X afterwards,you can delete it
with:

[B]sudo rm /etc/X11/xorg.conf
[/B]
(keep in mind or write down before..)


Edit:
BTW,"installing driver" as Ticcyca suggested,would be in System/Administration/,but,I think there is no Intel graphics driver.If so,install it.
Think editing xorg.conf might do the trick.

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> You could try a standart setting for intel.
Copy this:

[I]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/I]

into your empty xorg.conf file,restart.
If you -do not think so- cannot start X afterwards,you can delete it
with:

[B]sudo rm /etc/X11/xorg.conf
[/B]
(keep in mind or write down before..)


Edit:
BTW,"installing driver" as Ticcyca suggested,would be in System/Administration/,but,I think there is no Intel graphics driver.If so,install it.
Think editing xorg.conf might do the trick.

I tried to script in the xorg.conf file but sadly no luck. I also tried update update manager again with no luck.

Thanks for your suggestions.

---

### Post by realzippy on 2010-03-08
So have a look at xrandr,e.g.here:

[https://wiki.edubuntu.org/X/Config/Resolution](https://wiki.edubuntu.org/X/Config/Resolution)

If problems with that link,
post the outputs of:

```
xrandr
```

and

```
cvt 1024 768 85
```

---

### Post by realzippy on 2010-03-08
Just looked in synaptic...there is:

xserver-xorg-video-intel
You could try:

```
sudo apt-get install xserver-xorg-video-intel
```

but it should be installed already

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> Just looked in synaptic...there is:

xserver-xorg-video-intel
You could try:

```
sudo apt-get install xserver-xorg-video-intel
```but it should be installed already

I get the following :

anton@anton-Linux-desktop:~$ xrandr
Screen 0: minimum 320 x 200,  current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0  (normal left inverted right x axis y axis) 0mm x 0mm
    800x600        60.3* 
   640x480        59.9  
anton@anton-Linux-desktop:~$

anton@anton-Linux-desktop:~$  cvt 1024 768 85
# 1024x768 84.89 Hz (CVT 0.79M3) hsync: 68.68 kHz;  pclk: 94.50 MHz
Modeline "1024x768_85.00"   94.50  1024 1096 1200  1376  768 771 775 809 -hsync +vsync
anton@anton-Linux-desktop:~$


And

anton@anton-Linux-desktop:~$ sudo apt-get install  xserver-xorg-video-intel
[sudo] password for anton: 
Reading  package lists... Done
Building dependency tree       
Reading  state information... Done
xserver-xorg-video-intel is already the  newest version.
The following packages were automatically installed  and are no longer required:
  linux-headers-2.6.31-14  linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove  them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anton@anton-Linux-desktop:~$  

I hope this helps

Cheers

---

### Post by realzippy on 2010-03-08
Ok.Now:

```
xrandr --newmode "1024x768_85.00" 94.50 1024 1096 1200 1376 768 771 775 809 -hsync +vsync
```

then:

```
xrandr --addmode VGA1 "1024x768_85.00"
```

then test new resolution:

```
xrandr --output VGA1 --mode 1024x768_85.00
```

(it should also appear in settings/Display now.)

If it should work,you just need to make it persist reboot..

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> Ok.Now:

```
xrandr --newmode "1024x768_85.00" 94.50 1024 1096 1200 1376 768 771 775 809 -hsync +vsync
```then:

```
xrandr --addmode VGA1 "1024x768_85.00"
```then test new resolution:

```
xrandr --output VGA1 --mode 1024×768_85.00
```(it should also appear in settings/Display now.)

If it should work,you just need to make it persist reboot..


I typed in the commands : I got the following:

anton@anton-Linux-desktop:~$ xrandr --newmode "1024x768_85.00" 94.50  1024 1096 1200 1376 768 771 775 809 -hsync +vsync
anton@anton-Linux-desktop:~$  xrandr --addmode VGA1 "1024x768_85.00"
anton@anton-Linux-desktop:~$  xrandr --output VGA1 --mode 1024×768_85.00
xrandr: cannot find mode  1024×768_85.00
anton@anton-Linux-desktop:~$

I seems the mode can not be found.

I did a reboot it just in case it worked but again no luck

Cheers

---

### Post by realzippy on 2010-03-08
Please try again:

```
xrandr --output VGA1 --mode 1024x768_85.00
```

Sorry,mistyped × for x ....

But,as mentioned,you should also be able to select 1024x768 now in System/Settings/Display menue

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> Please try again:

```
xrandr --output VGA1 --mode 1024x768_85.00
```Sorry,mistyped × for x ....

But,as mentioned,you should also be able to select 1024x768 now in System/Settings/Display menue

I tried the code again and got:

anton@anton-Linux-desktop:~$ xrandr --output VGA1 --mode 1024x768_85.00
xrandr:  cannot find mode 1024x768_85.00
anton@anton-Linux-desktop:~$ 

Still not finding the mode.

Cheers

---

### Post by realzippy on 2010-03-08
makes

```
xrandr --output VGA1 --mode 1024x768
```

a difference?

But,as mentioned,you should also be able to select 1024x768 now in System/Settings/Display menue....??????????

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> makes

```
xrandr --output VGA1 --mode 1024x768
```a difference?

But,as mentioned,you should also be able to select 1024x768 now in System/Settings/Display menue....??????????

Still no luck:

anton@anton-Linux-desktop:~$ xrandr --output VGA1 --mode 1024x768
xrandr:  cannot find mode 1024x768
anton@anton-Linux-desktop:~$ 

There is still only the 2 selections 800x600 & 640x480

Cheers

[IMG]file:///C:/DOCUME%7E1/Anton/LOCALS%7E1/Temp/moz-screenshot.png[/IMG]

---

### Post by realzippy on 2010-03-08
??
Try again without the _85:

```
cvt 1024 768
```

```
xrandr --newmode "1024x768*your modeline from cvt*-hsync +vsync
```

```
xrandr --addmode VGA1 "1024x768"
```

```
xrandr --output VGA1 --mode 1024x768
```

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> ??
Try again without the _85:

```
cvt 1024 768
``````
xrandr --newmode "1024x768*your modeline from cvt*-hsync +vsync
``````
xrandr --addmode VGA1 "1024x768"
``````
xrandr --output VGA1 --mode 1024x768
```


Is this missing a quote ?

I get > appearing almost like the terminal is expecting somthing else??

Cheers

---

### Post by realzippy on 2010-03-08
> **Anton90125 said:**
> Is this missing a quote ?

I get > appearing almost like the terminal is expecting somthing else??

Cheers

xrandr --newmode "1024x768[COLOR="Cyan"]your modeline from cvt[/COLOR]-hsync +vsync

means that you should put the modeline from former given command [I]cvt 1024 768
[/I] in here.....e.g.:

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

---

### Post by Anton90125 on 2010-03-08
> **realzippy said:**
> xrandr --newmode "1024x768[COLOR=Cyan]your modeline from cvt[/COLOR]-hsync +vsync

means that you should put the modeline from former given command [I]cvt 1024 768
[/I] in here.....e.g.:

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

Thanks for explaing this.  I put the code in and got the following:

anton@anton-Linux-desktop:~$ xrandr --newmode "1024x768_60.00" 63.50  1024 1072 1176 1328 768 771 775 798 -hsync +vsync
X Error of failed  request:  BadName (named color or font does not exist)
  Major opcode  of failed request:  149 (RANDR)
  Minor opcode of failed request:   16 (RRCreateMode)
  Serial number of failed request:  21
  Current  serial number in output stream:  21
anton@anton-Linux-desktop:~$ 


Cheers

---

### Post by realzippy on 2010-03-09
[I]"anton@anton-Linux-desktop:~$ xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 149 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request: 21
Current serial number in output stream: 21
anton@anton-Linux-desktop:~$ "[/I]


...seems to be a bug xrandr is affected by.Same error happened 4 days ago in other resolution problem thread.There it could be solved by deleting non-existing modes (yes,sounds funny)....
Try this:

```
xrandr --delmode VGA1 "1024x768"
```

```
xrandr --delmode VGA1 "1024x768_85"
```

```
xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
```

```
xrandr --addmode VGA1 "1024x768"
```

```
xrandr --output VGA1 --mode 1024x768
```

---

### Post by Anton90125 on 2010-03-09
> **realzippy said:**
> [I]"anton@anton-Linux-desktop:~$ xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 149 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request: 21
Current serial number in output stream: 21
anton@anton-Linux-desktop:~$ "[/I]


...seems to be a bug xrandr is affected by.Same error happened 4 days ago in other resolution problem thread.There it could be solved by deleting non-existing modes (yes,sounds funny)....
Try this:

```
xrandr --delmode VGA1 "1024x768"
``````
xrandr --delmode VGA1 "1024x768_85"
``````
xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
``````
xrandr --addmode VGA1 "1024x768"
``````
xrandr --output VGA1 --mode 1024x768
```


Good Morning,

I just entered the code. Again it seems the modes are not recognised.

anton@anton-Linux-desktop:~$ xrandr --delmode VGA1 "1024x768"
xrandr:  cannot find mode "1024x768"
anton@anton-Linux-desktop:~$ xrandr  --delmode VGA1 "1024x768_85"
xrandr: cannot find mode "1024x768_85"
anton@anton-Linux-desktop:~$  xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775  798 -hsync +vsync
anton@anton-Linux-desktop:~$ xrandr --addmode VGA1  "1024x768"
xrandr: cannot find mode "1024x768"
anton@anton-Linux-desktop:~$  xrandr --output VGA1 --mode 1024x768
xrandr: cannot find mode  1024x768
anton@anton-Linux-desktop:~$ 

Cheers

---

### Post by realzippy on 2010-03-09
Good morning there,

running out of ideas.try:

```
xrandr --addmode VGA1 "1024x768_60.00" 
```

If no luck.last idea :
Create a test user (System/Administration/Users&groups),
should be a "desktop user"(no root/admin).Then login that new account,
and try again the steps.It happened that it worked in an added user account,
for unknown reason..

Also it is a good idea to open new thread,titled:

*Cannot increase resolution on Intel 82915G*



Sorry I cannot help you.

---

### Post by realzippy on 2010-03-09
1 last test:

```
gedit ~/Desktop/test
```

in the created file copy this:

[I]#!/bin/bash
xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr -s 1024x768[/I]

close and save the file.Then:

```
cd Desktop
```

```
sudo chmod +x test
```

```
sh test
```

---

### Post by Grenage on 2010-03-09
I have a rough and simple guide [here]("http://www.grenage.com/xorg.html"), take a look and work through the steps.

---

### Post by Anton90125 on 2010-03-09
> **realzippy said:**
> Good morning there,

running out of ideas.try:

```
xrandr --addmode VGA1 "1024x768_60.00" 
```If no luck.last idea :
Create a test user (System/Administration/Users&groups),
should be a "desktop user"(no root/admin).Then login that new account,
and try again the steps.It happened that it worked in an added user account,
for unknown reason..

Also it is a good idea to open new thread,titled:

*Cannot increase resolution on Intel 82915G*



Sorry I cannot help you.

Sadly these didn't work as well.

I will follow your suggestion and post another tread. Thanks for all your help I really appricate it!

Cheers

Anton

---

### Post by Anton90125 on 2010-03-09
I think I solved it!

I added 

Modeline "1024x768_85.00"   94.50  1024 1096 1200  1376  768 771 775 809  -hsync +vsync

to the xorg.conf file under Monitor.

This seems to have worked. Now I have to think about how to get the imaged centred now.

---

### Post by Anton90125 on 2010-03-09
> **Grenage said:**
> I have a rough and simple guide [here]("http://www.grenage.com/xorg.html"), take a look and work through the steps.

Sorry I missed this!

I am just disgusting this now. Thanks!

---

### Post by Grenage on 2010-03-09
> **Anton90125 said:**
> Sorry I missed this!

I am just **disgusting** this now. Thanks!

Harsh! ;)

---

### Post by Anton90125 on 2010-03-09
> **Grenage said:**
> Harsh! ;)

That was meant to read digesting. I can not type at speed and when I get excited!!!

---

### Post by realzippy on 2010-03-10
Great you made it!Can you post your solution (your xorg.conf)
so others will benefit?

---

### Post by Anton90125 on 2010-03-10
My final xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Driver  "intel"
EndSection

Section "Monitor"
Identifier "Configured  Monitor"
Modeline "1024x768_85.00" 94.50 1024 1096 1200 1376 768 771  775 809 -hsync +vsync
EndSection

Section "Screen"
Identifier  "Default Screen"
Monitor "Configured Monitor"
Device "Configured  Video Device"
DefaultDepth    24
    SubSection "Display"
         Depth           24
        Modes   "1280x768_85.0"
     EndSubSection


EndSection

---

### Post by Anton90125 on 2010-03-10
> **realzippy said:**
> Great you made it!Can you post your solution (your xorg.conf)
so others will benefit?

Though this may seem a but masochistic (spelling??) I enjoyed looking into this problem, I have learnt alot from it.

---

### Post by COKEDUDE on 2010-10-27
> xrandr: cannot find mode 1024×768

I see a lot of people are having trouble with this. 

In Linux capitalization is VERY important. Here you guys did not capitalize your the "X" in your resolution. Once you capitalize your "X" you should be good. Here is an example of what worked for me. 

```
xrandr --output VGA1 --mode 1024x768 --rate 60
```

---

