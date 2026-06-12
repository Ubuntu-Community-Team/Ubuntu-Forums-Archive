---
title: "Nvidia Optimus - Bumblebee or Ironhide?"
date: 2011-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by baby_panda on 2011-10-28
Hi, I have a Dell XPS L501X laptop. It has nVidia GeForce GT420M graphics card which uses Optimus. My OS is Ubuntu 11.10 (32 bit). I have read that currently the only way to use Optimus graphic cards in Ubuntu is to install Bumblebee or Ironhide. Which one of these is better? I want stable software that does not crash my system. Should I install nVidia driver from official repository (nvidia-current) or ppa:ubuntu-x-swat/x-updates? Also, which profile should I use for configuring Bumblebee/Ironhide? Thanks.

---

### Post by akoskm on 2011-10-28
Just come over on optimus problems in the past few days (525 M).
I installed ironhide (I read somewhere that it is the next version of bumblebee, codenamed like that).
Don't install any of the restricted drivers like nvidia-current and such, ironhide will take care about those things.
You will find the basic instructions about enabling your cards on the project site:
[http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html](http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html)

Good luck.

---

### Post by moldaviax on 2011-10-29
hi
I haven't tried either of those yet, just found out about ironhide the other day.
Do they require the nouveau driver? I thought the nvidia drivers were on the whole recommended over nouveau for power consumption etc?

M.

---

### Post by akoskm on 2011-10-29
> **moldaviax said:**
> hi
I haven't tried either of those yet, just found out about ironhide the other day.
Do they require the nouveau driver? I thought the nvidia drivers were on the whole recommended over nouveau for power consumption etc?

M.

No, they require the official nvidia drivers. I just warned you to don't install anything by "hand", ironhide will take care about the drivers.

---

### Post by jocheem67 on 2011-10-29
I've been using bumblebee on arch > drawback is that it provided no energysaving-features. That might have changed though ans is worth looking into. 
I use acpi_call with success. This disables the nvidia and just addresses the intel graphic chip. That's on linux mint based on 10.04. It needs some configuration though. Advantage is that it's a good solution regarding powerconsumption on my dell xps15 ( 502 )..
I've got no need to use the nvidia 520 as I still have win7 installed for the heavier duties. 
I guess it all depends on your needs. If you wanna use the nvidia , then ironhide or bumblebee, otherwise I'd say look into the acpi_call method.

---

### Post by akoskm on 2011-10-30
For the same reason I switched to win 7, ironhide failed to disable my nvidia card, so wasn't really power saving. I also managed to got a free copy of windows through the Academic Alliance program on my university, so in long term this was cheaper solution.
Regardless my current current OS I'm looking forward for the improvements on the field of hybrid graphics on Linux, I've been using only linux for more than 5 years..

---

### Post by foxy123 on 2011-10-30
> **akoskm said:**
> For the same reason I switched to win 7, ironhide failed to disable my nvidia card, so wasn't really power saving. I also managed to got a free copy of windows through the Academic Alliance program on my university, so in long term this was cheaper solution.
Regardless my current current OS I'm looking forward for the improvements on the field of hybrid graphics on Linux, I've been using only linux for more than 5 years..

So you can't disable nVidia card using Ironhide?

---

### Post by akoskm on 2011-10-30
> **foxy123 said:**
> So you can't disable nVidia card using Ironhide?

IIRC when I opened the ironhide-settings and and tried to modify the power saving options, whatever I chose it said that disabling the card failed, like in the test what I linked here:
[http://ubuntuforums.org/showpost.php?p=11402410&postcount=2](http://ubuntuforums.org/showpost.php?p=11402410&postcount=2)

---

### Post by foxy123 on 2011-10-30
> **akoskm said:**
> IIRC when I opened the ironhide-settings and and tried to modify the power saving options, whatever I chose it said that disabling the card failed, like in the test what I linked here:
[http://ubuntuforums.org/showpost.php?p=11402410&postcount=2](http://ubuntuforums.org/showpost.php?p=11402410&postcount=2)

I've got as follows but don't know what it means (I don't have glxgears but glxsheres):
```
~$ optirun glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x94
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ironlake Mobile 
19.536200 frames/sec - 21.802399 Mpixels/sec
19.755290 frames/sec - 22.046904 Mpixels/sec
19.651736 frames/sec - 21.931338 Mpixels/sec
19.941070 frames/sec - 22.254234 Mpixels/sec
19.940653 frames/sec - 22.253769 Mpixels/sec
19.939750 frames/sec - 22.252761 Mpixels/sec
19.946976 frames/sec - 22.260825 Mpixels/sec
19.935810 frames/sec - 22.248364 Mpixels/sec
19.944216 frames/sec - 22.257745 Mpixels/sec
19.937466 frames/sec - 22.250212 Mpixels/sec
19.944045 frames/sec - 22.257554 Mpixels/sec
19.945949 frames/sec - 22.259679 Mpixels/sec
19.935601 frames/sec - 22.248131 Mpixels/sec
19.937293 frames/sec - 22.250019 Mpixels/sec
19.779300 frames/sec - 22.073699 Mpixels/sec
19.917491 frames/sec - 22.227920 Mpixels/sec
19.796578 frames/sec - 22.092981 Mpixels/sec
19.778818 frames/sec - 22.073161 Mpixels/sec
^Z
[1]+  Stopped                 optirun glxspheres

```

---

### Post by akoskm on 2011-10-30
You are getting low framerates, look like only intel is working (OpenGL Renderer: Mesa DRI Intel(R) Ironlake Mobile).
In my test I got around ~1k which indicates that the nvidia card was  working too, however I'm not sure should it switch on by default on such test like glxspheres...

---

### Post by foxy123 on 2011-10-30
> **akoskm said:**
> You are getting low framerates, look like only intel is working (OpenGL Renderer: Mesa DRI Intel(R) Ironlake Mobile).
In my test I got around ~1k which indicates that the nvidia card was  working too, however I'm not sure should it switch on by default on such test like glxspheres...

Thanks. Intel-only is fine by me for now. To be honest I could not figure out when settings I should use in Ironhide during installation.

---

### Post by baby_panda on 2011-10-30
Hi, I installed Bumblebee from stable ppa. I used nVidia driver from official repository (not ppa:ubuntu-x-swat/x-updates). When I used optirun, it shows error message "Bumblebee X server failed to start" and "Failed to initialize nVidia GPU at PCI:2:0:0" in /var/log/Xorg.8.log. Then I activated nvidia-current and nvidia-current-updates in Additional Drivers. Now glxspheres, glxgears, etc. won't work without optirun! Also the Unity interface now displays with some errors. Any ideas why Bumblebee did not work? Thanks.

P.S.:My laptop configurations are given in the first message in this thread.

---

### Post by akoskm on 2011-10-30
> **baby_panda said:**
> Hi, I installed Bumblebee from stable ppa. I used nVidia driver from official repository (not ppa:ubuntu-x-swat/x-updates).
...


> **akoskm said:**
> ...
Don't install any of the restricted drivers like nvidia-current and such, ironhide will take care about those things.
You will find the basic instructions about enabling your cards on the project site:
[http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html](http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html)

Good luck.

You should wipe out everything related to nvidia and read my first post again.

---

### Post by baby_panda on 2011-10-30
> **akoskm said:**
> You should wipe out everything related to nvidia and read my first post again.
Hi, I think I should clarify. I initially installed Bumblebee without manually installing the nvidia-current driver. nvidia-current was fetched automatically by the package manager during installation. Then it showed the error "Bumblebee X server failed to start". After that, I manually activated the nvidia-current and nvidia-current-updates drivers in Additional Drivers. Still some other errors occurred as mentioned in my previous message.

---

### Post by akoskm on 2011-10-30
> **baby_panda said:**
> Hi, I think I should clarify. I initially installed Bumblebee without manually installing the nvidia-current driver. nvidia-current was fetched automatically by the package manager during installation. Then it showed the error "Bumblebee X server failed to start". After that, I manually activated the nvidia-current and nvidia-current-updates drivers in Additional Drivers. Still some other errors occurred as mentioned in my previous message.

In Additional drivers dialog both nvidia-current and nvidia-current-updates are inactive after installing ironhide (not sure about bumblebee).
Anyway, so far we were talking about Ironhide, have you tried to install that?

---

### Post by Donce on 2011-11-02
I installed ironhide, but I got many errors during installation end. I even get errors while disabling and enabling card. I get this with ironhide-disablecard:
```

ERROR: Module nvidia_current does not exist in /proc/modules
_DSM Disabling nVidia card succeeded.
_PS3 Disabling nVidia card succeeded.

```
And this with ironhide-enablecard:
```

_PS0 Enabling nVidia card succeeded.
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic-pae/updates/dkms/nvidia_current.ko): No such device

```
But still, laptop gets much cooler and more quiet instantly, ironhide seems to be working for me! :)
I have Dell Inspiron N5110 with i3-2310M and Nvidia 525M.

---

### Post by akoskm on 2011-11-04
> **Donce said:**
> I installed ironhide, but I got many errors during installation end. I even get errors while disabling and enabling card. I get this with ironhide-disablecard:
```

ERROR: Module nvidia_current does not exist in /proc/modules
_DSM Disabling nVidia card succeeded.
_PS3 Disabling nVidia card succeeded.

```
And this with ironhide-enablecard:
```

_PS0 Enabling nVidia card succeeded.
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic-pae/updates/dkms/nvidia_current.ko): No such device

```
But still, laptop gets much cooler and more quiet instantly, ironhide seems to be working for me! :)
I have Dell Inspiron N5110 with i3-2310M and Nvidia 525M.

Hi!
Same thing happened to me, same configuration (except that this is i5). I don't know any reliable solutions for this so far. The truth is that my both cards were running at the same time, regardless to the events.

---

### Post by chukis13 on 2011-11-06
So is Ironhide still the latest and most updated? Or is the Bumblebee project? Will either of these work with 10.04?

---

### Post by SavageCHRIS on 2011-11-06
I've got Bumblebee project working fine on 11.10 with power management by following this guide [http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

---

### Post by chukis13 on 2011-11-07
> **SavageCHRIS said:**
> I've got Bumblebee project working fine on 11.10 with power management by following this guide [http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

Anyone know if this will work with 10.10? I'm new to Ubuntu so I'm not too sure. Also, should I just go ahead and upgrade all the way to 11.10? Is it stable now?

---

### Post by SavageCHRIS on 2011-11-10
> **chukis13 said:**
> Anyone know if this will work with 10.10? I'm new to Ubuntu so I'm not too sure. Also, should I just go ahead and upgrade all the way to 11.10? Is it stable now?
I'm not sure if it works for 10.10 but I would advise you to update to 11.10, its more supported for newer hardware.

I'm using it on my Optimus laptop, its very stable and works great

---

### Post by erickjbc on 2011-11-27
> **Donce said:**
> I installed ironhide, but I got many errors during installation end. I even get errors while disabling and enabling card. I get this with ironhide-disablecard:
```

ERROR: Module nvidia_current does not exist in /proc/modules
_DSM Disabling nVidia card succeeded.
_PS3 Disabling nVidia card succeeded.

```
And this with ironhide-enablecard:
```

_PS0 Enabling nVidia card succeeded.
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic-pae/updates/dkms/nvidia_current.ko): No such device

```
But still, laptop gets much cooler and more quiet instantly, ironhide seems to be working for me! :)
I have Dell Inspiron N5110 with i3-2310M and Nvidia 525M.

I have a Dell XPS15-L502x with GT 525M and Ubuntu 11.10, I got Ironhide installed and got the same problem as you but managed to fix it doing the following:

1. Go into /etc/default/ironhide and open it
2. change IRONHIDE_ACPI_MODE=1 to IRONHIDE_ACPI_MODE=0
3. save file
4. reboot

When I do the test I get the following:

```
:~$ optirun glxspheres
 * Starting Ironhide X server ironhide                                          _PS0 Enabling nVidia Card Succeded.
.                                                                        [ OK ]
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 525M/PCI/SSE2
103.090972 frames/sec - 115.049525 Mpixels/sec
108.465826 frames/sec - 121.047861 Mpixels/sec
106.642111 frames/sec - 119.012596 Mpixels/sec
113.420092 frames/sec - 126.576823 Mpixels/sec
103.902484 frames/sec - 115.955172 Mpixels/sec
110.651463 frames/sec - 123.487032 Mpixels/sec
107.673969 frames/sec - 120.164149 Mpixels/sec
105.652561 frames/sec - 117.908258 Mpixels/sec
102.425921 frames/sec - 114.307328 Mpixels/sec
110.850360 frames/sec - 123.709002 Mpixels/sec
104.759475 frames/sec - 116.911574 Mpixels/sec
105.474076 frames/sec - 117.709069 Mpixels/sec
 * Stopping Ironhide X server ironhide                                          _PS0 Disabling nVidia Card Succeded.
                                                                         [ OK ]
```

So I think it is working. Can someone tell me if im right?

---

### Post by BjBlaster on 2011-11-29
> **chukis13 said:**
> So is Ironhide still the latest and most updated? Or is the Bumblebee project? Will either of these work with 10.04?

I'd also like to know what works for 10.04 LTS? I've upgraded to the latest 3.01 kernel, but can't get a repo that works with 10.04 regardless.... That would be a pitty because I don't like gnome3 or unity all that much ;(

---

### Post by metasoarous on 2011-12-15
> **BjBlaster said:**
> .... That would be a pitty because I don't like gnome3 or unity all that much ;(

Don't let that prevent you from upgrading. You can still run the classic Gnome. Also, I'm betting it's probably Gnome Shell that you don't like. Gnome3 is just the underlying system for Gnome3, but can still be made to run in the classic mode without the "Shell".

---

### Post by danger89 on 2012-01-14
Bumblebee 3.0 is out now!

---

### Post by hayhursm on 2012-01-16
Hello everyone,

I have a Toshiba Satellite (P755-S5269) running Linux Mint 12 x64 with Nvidia GeForce GT 540M and Intel Sandybridge Mobile chipsets.  I first installed Bumblebee but laptop would still boot to a blank screen (unless I deleted my xorg.conf).  I installed Ironhide and everything worked great!!  Here are the test runs:

[B]$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x94
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
59.896267 frames/sec - 50.950161 Mpixels/sec
59.871879 frames/sec - 50.929415 Mpixels/sec
59.864174 frames/sec - 50.922861 Mpixels/sec
59.860080 frames/sec - 50.919378 Mpixels/sec
59.883226 frames/sec - 50.939068 Mpixels/sec
59.838203 frames/sec - 50.900769 Mpixels/sec
[/B]
[B]$ optirun glxspheres
 * Starting Ironhide X server ironhide                                          .                                                                        [ OK ]
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCI/SSE2
140.478485 frames/sec - 119.496619 Mpixels/sec
141.778694 frames/sec - 120.602628 Mpixels/sec
149.798747 frames/sec - 127.424806 Mpixels/sec
149.987234 frames/sec - 127.585141 Mpixels/sec
146.639581 frames/sec - 124.737493 Mpixels/sec
153.747310 frames/sec - 130.783612 Mpixels/sec
138.094160 frames/sec - 117.468416 Mpixels/sec
143.970721 frames/sec - 122.467254 Mpixels/sec
[/B]
By chance does anyone have a working power on/off control script for this model laptop?  After installing Ironhide I received a message: **"No power-on/off configuration has been reported for your machine please manually enter configuration in: /usr/local/bin/ironhide-enablecard and /usr/local/bin/ironhide-disablecard**"  I'm still in the newbie stages of Linux and I've looked at the example control scripts but I'm lost.  Also, am I right in assuming these configuration files automate the task of switching between discrete and integrated graphics modes?

---

### Post by 23dornot23d on 2012-01-26
I just got a new computer Asus K53SV

the graphics Nvidia GT540M ...... 

Running Natty ....

I tried everything I could before finding this thread to no avail ....

But now .... a big :) 

I used ironhide ..... and the configuration that most users seem to have got 
things working with.

Here are my results .... so far ... only set it up a few hours ago .... but am very
happy now.

keith@keith-K53SV:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x96
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
29.643976 frames/sec - 24.664974 Mpixels/sec
29.493967 frames/sec - 24.540160 Mpixels/sec
keith@keith-K53SV:~$ optirun glxspheres
 * Starting Ironhide X server ironhide                                          _PS0 Enabling nVidia Card Succeded.
DGPS Enabling nVidia Card Succeded.
.                                                                        [ OK ]
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCI/SSE2
99.568166 frames/sec - 82.844697 Mpixels/sec
90.712818 frames/sec - 75.476693 Mpixels/sec
 * Stopping Ironhide X server ironhide                                          _DSM Disabling nVidia Card Succeded.
_PS3 Disabling nVidia Card Succeded.
DGPS Disabling nVidia Card Succeded.
                                                                         [ OK ]
keith@keith-K53SV:~$ 


All seems to be working well .... it comes in when I need it now ..... for 3D etc ...

---

### Post by hayhursm on 2012-01-26
> **23dornot23d said:**
> I just got a new computer Asus K53SV

the graphics Nvidia GT540M ...... 

Running Natty ....

I tried everything I could before finding this thread to no avail ....

But now .... a big :) 

I used ironhide ..... and the configuration that most users seem to have got 
things working with.

Here are my results .... so far ... only set it up a few hours ago .... but am very
happy now.

keith@keith-K53SV:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x96
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
29.643976 frames/sec - 24.664974 Mpixels/sec
29.493967 frames/sec - 24.540160 Mpixels/sec
keith@keith-K53SV:~$ optirun glxspheres
 * Starting Ironhide X server ironhide                                          _PS0 Enabling nVidia Card Succeded.
DGPS Enabling nVidia Card Succeded.
.                                                                        [ OK ]
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCI/SSE2
99.568166 frames/sec - 82.844697 Mpixels/sec
90.712818 frames/sec - 75.476693 Mpixels/sec
 * Stopping Ironhide X server ironhide                                          _DSM Disabling nVidia Card Succeded.
_PS3 Disabling nVidia Card Succeded.
DGPS Disabling nVidia Card Succeded.
                                                                         [ OK ]
keith@keith-K53SV:~$ 


All seems to be working well .... it comes in when I need it now ..... for 3D etc ...


Could you please post your **ironhide-enablecard **and** ironhide-disablecard** control scripts?  I am running into this problem now:

**satellite-p755 ~ $ glxspheres **
Polygons in scene: 62464
Visual ID of window: 0x94
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
59.690547 frames/sec - 50.775167 Mpixels/sec
59.847866 frames/sec - 50.908988 Mpixels/sec
59.865170 frames/sec - 50.923709 Mpixels/sec
59.864081 frames/sec - 50.922782 Mpixels/sec
59.863668 frames/sec - 50.922431 Mpixels/sec
59.862009 frames/sec - 50.921019 Mpixels/sec
59.863924 frames/sec - 50.922649 Mpixels/sec
59.861895 frames/sec - 50.920923 Mpixels/sec
59.864416 frames/sec - 50.923067 Mpixels/sec
[B]
satellite-p755 ~ $ optirun glxspheres[/B]
 * Starting Ironhide X server ironhide                                                                     _PS0 Enabling nVidia card succeeded.
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-15-generic/kernel/drivers/char/drm/nvidia_current.ko): No such device
... * The nvidia driver was not loaded, try: sudo modprobe nvidia-current                                   
* The Ironhide Xserver failed to start. Please check /var/log/Xorg.8.log                           [fail] 
ironhide could not be started - optirun cannot be executed.

---

### Post by 23dornot23d on 2012-01-26
> 
Could you please post your **ironhide-enablecard **and** ironhide-disablecard** control scripts?  I am running into this problem now:
I will if you let me know where I can find them .......

not sure where they are .... what directory should I look in for them ...... ?  :confused:

found them

ENABLECARD=/usr/local/bin/ironhide-enablecard

> 
#!/bin/bash
# This script should contain the command(s) nessesary to switch on the
# nVidia card.
# As an example i've included the script for some Asus machines..
# Please note that the acpi_call module is need for these operations:
#
# [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
#
# calls originally for Asus 1215N by Pete Eberlein
# modified by Thomas Krutz to fix fullspeed fanspeed issue on Asus K53SV-family

modprobe acpi_call

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    result=$(cat /proc/acpi/call)
    case "$result" in
     Error*)
      echo "Enabling nVidia Card failed ($result)."
      ;;
     *)
      echo "Enabling nVidia Card Succeded."
     ;;
    esac
}

echo _PS0 $(acpi_call "\_SB.PCI0.PEGR.GFX0._PS0")
echo DGPS $(acpi_call "\_SB.PCI0.PEGR.GFX0.DGPS")

modprobe nvidia-current

DISABLECARD=/usr/local/bin/ironhide-disablecard


> 
#!/bin/bash
# This script should contain the command(s) nessesary to switch off the
# nVidia card.
# As an example i've included the script for the Asus machines..
# Please note that the acpi_call module is need for these operations:
#
# [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
#
# calls originally for Asus 1215N by Pete Eberlein
# modified by Thomas Krutz to fix fullspeed fanspeed issue on Asus K53SV-family

rmmod nvidia
if lsmod | grep -q nvidia; then
 echo "Error: could not unload nvidia module, leaving card turned on"
 exit
fi
modprobe acpi_call

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    result=$(cat /proc/acpi/call)
    case "$result" in
     Error*)       
      echo "Disabling nVidia Card failed ($result)."
      ;;                          
     *)                                   
      echo "Disabling nVidia Card Succeded."                                                                                
     ;;                                                                   
    esac   
}

echo _DSM $(acpi_call "\_SB.PCI0.PEGR.GFX0._DSM" \
    "{0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47," \
     "0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0}" \
     "0x100 0x1A {0x1,0x0,0x0,0x3}")
    # ok to turn off: Buffer {0x59 0x0 0x0 0x11}
    # is already off: Buffer {0x41 0x0 0x0 0x11}
echo _PS3 $(acpi_call "\_SB.PCI0.PEGR.GFX0._PS3")
echo DGPS $(acpi_call "\_SB.PCI0.PEGR.GFX0.DGPS")

I am running a older kernel .... and natty ......
[COLOR=Red][B]
  I am running 2.6.38-13-generic[/B][/COLOR] 
(not that I know there is anything in the later kernel that should cause problems)

> 
deb [http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu](http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu) natty main 

deb-src [http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu](http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu) natty main 

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main  

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main                                              

Looks more like something is missing ..... in yours .... but no idea why .... the only other thing I did was to add the xorg-edgers ppa

FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-15-generic/kernel/drivers/char/drm/nvidia_current.ko): No such device


Facebook has a thread running on this too ....
[http://www.facebook.com/pages/Ironhide-nVidia-Optimus-Support-for-Linux/128977617199105?sk=wall&filter=12](http://www.facebook.com/pages/Ironhide-nVidia-Optimus-Support-for-Linux/128977617199105?sk=wall&filter=12)

---

### Post by hayhursm on 2012-01-26
> **23dornot23d said:**
> I will if you let me know where I can find them .......

not sure where they are .... what directory should I look in for them ...... ?  :confused:

found them

ENABLECARD=/usr/local/bin/ironhide-enablecard
DISABLECARD=/usr/local/bin/ironhide-disablecard


Yes, that's the them...could you please open them with a text editor such as **gedit** and post the contents or attach as a file?   Thanks!

---

### Post by 23dornot23d on 2012-01-26
I edited the thread and added them .....

you must have posted as I was cutting and pasting them into place

[http://ubuntuforums.org/showpost.php?p=11642437&postcount=29](http://ubuntuforums.org/showpost.php?p=11642437&postcount=29)


> 64 bit thread
[http://ubuntuforums.org/showthread.php?t=1875982](http://ubuntuforums.org/showthread.php?t=1875982)

Check this out too ....

[http://www.martin-juhl.dk/2011/10/moving-to-oneironhide/](http://www.martin-juhl.dk/2011/10/moving-to-oneironhide/)



[COLOR=Red]**Issues are reported here**[/COLOR]

[https://github.com/MrMEEE/ironhide/issues](https://github.com/MrMEEE/ironhide/issues)

---

### Post by edschneider on 2012-02-16
> **erickjbc said:**
> I have a Dell XPS15-L502x with GT 525M and Ubuntu 11.10, I got Ironhide installed and got the same problem as you but managed to fix it doing the following:

1. Go into /etc/default/ironhide and open it
2. change IRONHIDE_ACPI_MODE=1 to IRONHIDE_ACPI_MODE=0
3. save file
4. reboot

When I do the test I get the following:

```
:~$ optirun glxspheres
 * Starting Ironhide X server ironhide                                          _PS0 Enabling nVidia Card Succeded.
.                                                                        [ OK ]
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 525M/PCI/SSE2
103.090972 frames/sec - 115.049525 Mpixels/sec
108.465826 frames/sec - 121.047861 Mpixels/sec
106.642111 frames/sec - 119.012596 Mpixels/sec
113.420092 frames/sec - 126.576823 Mpixels/sec
103.902484 frames/sec - 115.955172 Mpixels/sec
110.651463 frames/sec - 123.487032 Mpixels/sec
107.673969 frames/sec - 120.164149 Mpixels/sec
105.652561 frames/sec - 117.908258 Mpixels/sec
102.425921 frames/sec - 114.307328 Mpixels/sec
110.850360 frames/sec - 123.709002 Mpixels/sec
104.759475 frames/sec - 116.911574 Mpixels/sec
105.474076 frames/sec - 117.709069 Mpixels/sec
 * Stopping Ironhide X server ironhide                                          _PS0 Disabling nVidia Card Succeded.
                                                                         [ OK ]
```

So I think it is working. Can someone tell me if im right?

Thanks!

My "optimus" on Ubuntu 11.10 is working now on my Dell XPS 15 L502X with nvidia GT525M.

---

