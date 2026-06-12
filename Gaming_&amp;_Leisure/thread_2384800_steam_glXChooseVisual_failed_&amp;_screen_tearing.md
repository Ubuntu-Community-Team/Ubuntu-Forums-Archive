---
title: "steam glXChooseVisual failed &amp; screen tearing"
date: 2018-02-12
forum: Gaming &amp; Leisure
---

### Post by dutchen18 on 2018-02-12
Let's start with a hardware list:
[LIST]
[*]CPU : Intel(R) Core(TM) i7-3632QM @ 2.20GHz 
[*]GPU1 : Intel HD graphics 4000 (lshw just shows "3rd Gen Core processor Graphics Controller", which might be because of drivers issues, but i don't really care since wont be using this GPU for anything high performance anyways) 
[*]GPU2 : GK107M [GeForce GT 650M] 
[/LIST]
Probably irrelevant hardware:
[LIST]
[*]MEMORY : 8GiB of DDR3 @ 1600MHz (again the lshw listing confuses me) 
[*]DISK : 931GiB TOSHIBA MQ01ABD1 on /dev/sda (only 100GiB reserved for ubuntu) 
[*]CDROM : CDDVDW SN-208AB (partially broken) 
[*]ETHERNET : RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
[*]WIRELESS : Intel Centrino Wireless-N 135 
[/LIST]
If you haven't noticed yet by some of the hardware, it's a laptop.

After a bunch of fiddling with nvidia drivers and nvidia-prime i managed to get my system to run on my 650M instead of the intel GPU, but this introduced some other problems (i love lists):
[LIST=1]
[*]steam shows "glXChooseVisual failed" on startup, i'm guessing this is because steam is a 32 bit application and i don't have the 32 bit nvidia drivers installed. "Well why don't you just install those?" i hear you ask, well:
```
# apt-get install nvidia-390:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-390:i386 : Depends: make:i386
                   Depends: xserver-xorg-legacy:i386
                   Depends: xorg-video-abi-11:i386 but it is not installable or
                            xorg-video-abi-12:i386 but it is not installable or
                            xorg-video-abi-13:i386 but it is not installable or
                            xorg-video-abi-14:i386 but it is not installable or
                            xorg-video-abi-15:i386 but it is not installable or
                            xorg-video-abi-18:i386 but it is not installable or
                            xorg-video-abi-19:i386 but it is not installable or
                            xorg-video-abi-20:i386 or
                            xorg-video-abi-23:i386
                   Depends: xserver-xorg-core:i386
                   Recommends: nvidia-settings:i386 (>= 331.20) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
[IMG]https://i.imgur.com/xh698tW.png[/IMG]
Also note that steam runs fine when i select the intel GPU in nvidia-settings 
[*]Screen tearing, lot's and lot's of screen tearing. IT'S EVERYWHERE!
Running glxgears gives ~9600fps, which is 160 times the actual refresh rate, so no wonder there's screen tearing.
I've tried "Option "TripleBuffer" "True"" in the nvidia section of /etc/X11/xorg.conf
I've also tried "export __GL_YIELD="USLEEP"" in /etc/X11/profile.d/
I've also read that you might need to change something in nvidia-settings/OpenGL, but i don't have anything related to vsync in that section
[IMG]https://i.imgur.com/Zbitzfk.png[/IMG]
Just like the glXChooseVisual error, i've only noticed screen tearing when using the nvidia GPU. 
[/LIST]

---

