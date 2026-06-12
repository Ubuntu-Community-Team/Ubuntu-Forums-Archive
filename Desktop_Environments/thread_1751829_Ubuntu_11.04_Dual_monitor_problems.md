---
title: "Ubuntu 11.04 Dual monitor problems"
date: 2011-05-07
forum: Desktop Environments
---

### Post by qw3rty_rocks on 2011-05-07
I've been trying to get this working for a while now. I can get ubuntu to use two monitors, but with the new unity capabilities I can't drag any applications across. Whenever i try unity thinks i'm trying to make the window go to side on view (see attached). Is there a way around this.

---

### Post by marcoelgordo on 2011-05-07
Hi,

I have the same problem here. Unity seems to be the issue as when I log-in in Ubuntu Classic I can use the second monitor as an extended desktop.
Is there a fix or a configuration I need to enable in Unity.
I'm using a Geforce 8200 with the latest NVidia drivers 270.41.06.

Regards,

M

---

### Post by csmartdalton on 2011-05-11
I get the same thing with or without unity. My second monitor is useless. 

(When I launch a program in the 2nd monitor (i.e. right-click, "Change Desktop Background") the window has no borders, although I can resize it.)

---

### Post by Svip on 2011-05-12
> **csmartdalton said:**
> I get the same thing with or without unity. My second monitor is useless. 

(When I launch a program in the 2nd monitor (i.e. right-click, "Change Desktop Background") the window has no borders, although I can resize it.)

My fix for this is to add the following line into a start up script:

```
DISPLAY=:0 metacity --replace &
```

This fixes the window border issues for the second monitor.  But applets on the panels are still unusable.  I use Ubuntu Classic, by the way.  I need some serious start up scripts, because I have two monitors of different orientations (landscape, portrait).

---

### Post by Denizen08 on 2011-05-12
I get the same issue. Also, I connect to an external monitor whose resolution is larger than my laptop and need to place it at the left hand side rather than the right hand side. It's very glitchy and part of the screen is unreadable (for the second display).

---

### Post by VertigoRay on 2011-05-12
Previously, my second monitor was useless because it would simply not supply adequate power/hz despite the settings that I use.  My screen would blank out (power) regularly.  

That seems to be fixed with 11.04, but now the extended monitor checkbox has no effect. My second monitor remains a clone of my laptop screen.

Running ATI Mobility.

---

### Post by Asa J on 2011-05-13
Same here. major struggle. My second monitor is useless. Before at least it showed the background, now I can't even get it enabled.

---

### Post by MegaLoler on 2011-05-13
I can't get my second monitor to turn on or be detected either.  With or without unity.

---

### Post by oregonbob on 2011-05-18
I have same problem as Megaloler. My second monitor is not recognized but works just fine on Windows 7 (boo). Funny I just bought a new second monitor and now it is a paper weight.

---

### Post by Blasphemist on 2011-05-18
I've worked with a number of people on resolving issues like those described here, and resolved my own. I'm including a screen shot taken while dragging my browser from one screen to the other. This all does work but a number of different things can get in the way and therefore there are a number of different solutions. I recommend you start with a search, you can use this to make your results more specific [http://www.googlubuntu.com/](http://www.googlubuntu.com/), on your issue and gpu. You may well find an easy solution, or it could get complicated. If you then need assistance, please post a specific request and we'll be able to help.

---

### Post by oregonbob on 2011-05-18
Just after I typed above message I poked around and discovered my "NVidia X Server Settings" allowed me to find and recognize the second monitor. I am even using Unity. It was quirky at first but after a couple of reboots I think it is working.

---

### Post by Blasphemist on 2011-05-18
Great to hear!

---

### Post by fastnsilver on 2011-05-20
A colleague of mine wrote a simple script

> 
#!/bin/bash

if [ "$1" = "dock" ]; then
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080 --pos 0x0 --output HDMI3 --mode 1920x1080 --pos 1920x0
else 
xrandr --output VGA1 --off --output HDMI3 --off
xrandr --output LVDS1 --mode 1366x768 --pos 0x0
fi

unity --replace &


I have a Lenovo T510 laptop and a docking station.  The dockstation has 1 VGA and 1 HDMI port.  I have a Samsung 23" monitor connected to each port (i.e., 2 monitors total).  

Run the script after booting into Unity and docked with

> 
dockedMonitor.sh dock


Run the script without the "dock" param again to go back to just the laptop (i.e., when you're undocked).

Run 

> 
xrandr


to see what options are available for your particular setup, and update the script accordingly.

Note: if you're running Ubuntu Classic, then be sure to remove the last line of the script above.

---

### Post by ozicecool on 2011-05-23
Hi All,

I had some serious issues and pain in my upgrade from 10.10 to 11.04. Finally I got it going. (I posted a different thread on this) However as most of you I lost the connection to the 2nd monitor. After reading what some of you have done I managed to get the 2nd monitor back using Ubuntu Classic UI instead of Unity. Thanks for posting your findings. I am going to stick to Classic until Unity fixes the issues.

In case if you needed to know what PC I am running:
I have a DELL Studio 17" Laptop. However I am not using propritery ATI drivers instead I am going with the Open Source drivers. My 2nd Monitor is s 22" LG. They were both recognised in Unity, however I couldn't setup the 2nd Monitor with Unity. 

This is very strange as my colleague who uses a Fujistu Life notebook 15" uses ATI drivers and happily connected to the 2nd monitor with 11.04. He did have an issue in the initial upgrade complaining about 'flgrx' not available. However now all sorted and working. 

I also **_highly recommend_** that you have the home on a separate partition after what happened to me with the upgrades. While I managed to move to a new partition it was painful and I wasted almost 3 days sorting out these issues.

---

### Post by faustobm on 2011-05-30
Until 10.04 it worked fine but now with 11.04 I can't use two monitors.

---

### Post by jmatties on 2011-06-01
Same problem on Satellite M645 (PSMPMU-01201W) with Intel Integrated Graphics Controller [8086:0046].

Monitor is detected fine, and correct resolution is available, however only the top Unity bar shows on the external display; the rest is black. The mouse works everywhere on both screens, but the top portion of the main laptop screen is black. When dragging windows into the black area on either screen, the window disappears, but the mouse remains.

Dual screen worked **perfectly** with 10.10; it was awesome. Now it is unuseable :(

---

### Post by Blasphemist on 2011-06-02
> **jmatties said:**
> Same problem on Satellite M645 (PSMPMU-01201W) with Intel Integrated Graphics Controller [8086:0046].

Monitor is detected fine, and correct resolution is available, however only the top Unity bar shows on the external display; the rest is black. The mouse works everywhere on both screens, but the top portion of the main laptop screen is black. When dragging windows into the black area on either screen, the window disappears, but the mouse remains.

Dual screen worked **perfectly** with 10.10; it was awesome. Now it is unuseable :(

With natty came changes to grub, the kernel and xserver that are involved with what your are experiencing. Your configuration with actually 2 gpu's is maybe the most affected from what I've seen. I found this on your pc.
> Regardless, the Satellite M645 can still handle most modern games at the native 1366x768 screen resolution and thanks to Nvidia Optimus technology this notebook automatically switches between the Intel integrated graphics (for extended battery life) and the Nvidia dedicated graphics (for better video and gaming performance).
There is a project called debumblebee that you should look into. [https://github.com/z0rc/debumblebee#readme](https://github.com/z0rc/debumblebee#readme)
> This project allows you to utilize nVidia graphics card with proprietary driver
while running main desktop on Intel card. This service is only for Intel/nVidia
combination, it won't work with Intel/ATI or any other combination.

debumblebee is combination of additional X server for nVidia graphics card and
VirtualGL package which allows to access nVidia X server screen from Intel X
server screen with full OpenGL support.
I don't know exactly why this is now an issue and it is affecting many users so I expect more to be known and done soon.

---

### Post by dneff87 on 2011-06-02
I was having this problem on an HP G62 with ATI Mobility Radeon HD 4250 Graphics.

Today a new gdm (Gnome Desktop Manager) came through on update manager and fixed the problem. Everything now works as well as with 10.10 (dragging across screens included).

I suggest that everyone check it out and see if it helps.

Good luck!

Disclaimer: I don't know enough to help fix your problems (let alone many of my own), but this data point might help someone else come up with a solution.

---

### Post by XxX_VLAD_XxX on 2011-06-15
I believe the thing you need to edit is the Plug-In GRID under Compiz options.

Maybe you should take a look at that too.

---

### Post by badmanj32 on 2011-07-07
It looks like my laptop is trying it's darndest to give me an extended desktop but is failing.

I have a Dell Inspiron 640m
Graphics Card: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

My problem is that when I try to use extended desktop the display looks like it's being stretched and windows or buttons are not visible unless you hover over them. Then they display for a time but after a while it goes under the stretchy artifacts. (I've attached a screenshot of my extended desktop with said artifacts).

I've tried using Ubuntu with Unity and Ubuntu Classic and I get the same problems.

ALTHOUGH I've found that running in Ubuntu Classic (no effects) gives me a proper extended desktop. I tried turning stuff off in CompizConfigManager and re-attempting in Ubuntu Classic but it won't work.

Other than, "Get a new laptop" does anyone have any suggestions?

[IMG]https://lh5.googleusercontent.com/-dcWa8psp4BI/ThXKZtHhS5I/AAAAAAAAAGA/8eV6rc8FxP8/s1600/Screenshot.png[/IMG]

---

### Post by xnoxpx on 2011-07-26
> **fastnsilver said:**
> A colleague of mine wrote a simple script



I have a Lenovo T510 laptop and a docking station.  The dockstation has 1 VGA and 1 HDMI port.  I have a Samsung 23" monitor connected to each port (i.e., 2 monitors total).  

Run the script after booting into Unity and docked with



Run the script without the "dock" param again to go back to just the laptop (i.e., when you're undocked).

Run 



to see what options are available for your particular setup, and update the script accordingly.

Note: if you're running Ubuntu Classic, then be sure to remove the last line of the script above.

I have a Thinkpad T61 with a dock
My script is a little different, I've got it automatically running on login
first it checks for the dock (is there a display attached to DVI1) ?
if so first auto config DVI1, but turn everything else off, then pause for 3 seconds( if I don't do this I get unpredictable results)
Then make DVI1 the primary display with the secondary on the right, and keep the laptop display off.

if DVI1 isn't there, do nothing.

This way I don't have to manually run it each time I boot at work

```
#!/bin/bash
num=`xrandr|grep -c DVI1\ connected` 
if [ "$num" = "1" ] 
then 
 ` xrandr --output DVI1 --auto --output VGA1 --off --output LVDS1 --off`
sleep 3
 `xrandr --output DVI1 --auto --primary --left-of VGA1 --output VGA1 --auto --output LVDS1 --off`
fi

```

:confused:But I still don't know how to get the login screen to show on either of the external monitors,
:confused:I get bouncing "out of range" boxes, and I have to login blind
:confused:
:confused:

Edit: well for some reason the script stopped working correctly, it started giving me "mirrored" displays.
so I decided to force the "screen size" to be one monitor high x two monitors wide
 
```
#!/bin/bash
num=`xrandr|grep -c DVI1\ connected` 
if [ "$num" = "1" ] 
then 
 `xrandr -s 3840x1080 --output DVI1 --auto --primary --left-of VGA1 --output VGA1 --auto --output LVDS1 --off`
fi

```
It appears to work, I see how well it does over time.
still no idea how to get my login prompt to show on either @#$%#%^% external monitor !!!!

---

### Post by vhml76 on 2011-08-09
Hi everyone,

Same problem here. I have a Dell Vostro 3400 and the dual monitor option worked fine with Ubuntu 11.04 (unity) until I had to replace the LCD of my laptop due to a backlight burn out.

I had to set the external monitor (Samsung SyncMaster 2053sw VGA) as the primary monitor while my laptop screen was dead. I did this by turning off the laptop screen in System Settings -> Monitors. By doing this I can still work using the external monitor while the dell guys send a technician to look at my laptop screen problem.

The screen was replaced and since then, everytime I plug the external monitor to the VGA port both screens go black and I can no longer work. (dual monitor works fine in windows 7)

I have not activated the NVIDIA accelerated graphics driver since it has always caused problems with ubuntu 11.04 in my pc.

output of lshw -C display:
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: GT218 [GeForce 310M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f9000000-f9ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128 ) memory:fa000000-fa07ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fa400000-fa7fffff memory:b0000000-bfffffff ioport:f080(size= 8)

output of cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Thanks for your help,

---

### Post by xnoxpx on 2011-08-15
vhml76, shooting from the hip,do you know  the "technician" updated the bios after the screen replacement?
does Fn F8 cycle through (pre OS(during POST), as well as after Ubuntu loads)
1) laptop display
2) external display
3) both displays ?

if you go into setup (F12 ? while "dell" splash is shown) are there any settings regarding the display/ hot keys/ or OS capabilities ?

---

### Post by xnoxpx on 2011-08-15
I finally found a way to get the gdm login screen to use my external monitors.
I add a line to /etc/gdm/Init/Default right before (/sbin/initctl .......)
that executed a bash script, stumbled someone else's attempt (successful) and they added the code right there (duh)
So here is what got my external displays to show the login prompt
("/sbin/initctl ......." already existed)
```
DVI1_PRESENT=`xrandr | grep "DVI1 connected"`
if [ "x${DVI1_PRESENT}x" != "xx" ]; then
xrandr --output DVI1 --auto --pos 0x0 --primary
xrandr --output LVDS1 --off
xrandr --output VGA1 --auto --right-of DVI1
fi

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm

```

---

### Post by vhml76 on 2011-08-15
> **xnoxpx said:**
> vhml76, shooting from the hip,do you know  the "technician" updated the bios after the screen replacement?
does Fn F8 cycle through (pre OS(during POST), as well as after Ubuntu loads)
1) laptop display
2) external display
3) both displays ?

if you go into setup (F12 ? while "dell" splash is shown) are there any settings regarding the display/ hot keys/ or OS capabilities ?


Hi,

I solved my problem by creating a new user and moving all my files to my new user account. Dual monitor works fine with my new user account... a shot in the dark. ;-)

---

