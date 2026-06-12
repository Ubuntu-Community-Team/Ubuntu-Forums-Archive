---
title: "Hulu in fullscreen VERY choppy Jaunty 9.04"
date: 2009-05-01
forum: Desktop Environments
---

### Post by headlice on 2009-05-01
Hi,

I had upgraded from Ubuntu 8.10 to 9.04.

Hulu was working GREAT in 8.10 in fullscreen mode.  After the upgrade, Hulu is unwatchable in fullscreen mode.  The video lags GREATLY behind the sound.

Even Boxee has delayed/slow response to they keyboard.  Could this be a flash issue?  If so, I didnt have this problem with 8.10 and was using the same flash version and everything....

Anyone else?  Anyone solve this?  I checked this forum and google and have not come across anything like this for Jaunty.

---

### Post by Cybie257 on 2009-05-01
What video card are you using? This could have a lot to do with it as some of the older ATI and nVidia cards are no longer supported with proprietary drivers as of Jaunty. 

Begin by giving some specs in order for better help. I'm using an ATI X1300T with choppy results when I expand the screen, but full screen seems to do better as long as I leave the computer alone. I'm using dual screens, so tend to work on the other while something else is playing. 

-Cybie

---

### Post by headlice on 2009-05-01
Using an Acer Aspire 5600 notebook with stock video and audio:

```
*-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

---

### Post by tjeremiah on 2009-05-02
Intel and Ubuntu dont seem to like each other. Ive had this problem since 8.10 with screen tearing and with 9.04, the problem is worst. Maybe this bug report I filled out can help? The more response to it, the faster I think it will get fixed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359124](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359124)

---

### Post by Cybie257 on 2009-05-02
Just thought of something. Do you have desktop/visual effects turned on? f so, try turning it off (or to : None) and see if that helps. 


System->Preferences->Appearance "Visual Effects Tab"

-Cybie

---

### Post by inobe on 2009-05-02
check out this pinned intel performance article, many have fixed performance issues.

read [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by headlice on 2009-05-02
> **Cybie257 said:**
> Just thought of something. Do you have desktop/visual effects turned on? f so, try turning it off (or to : None) and see if that helps. 


System->Preferences->Appearance "Visual Effects Tab"

-Cybie

I tried that.  Still no go.

---

### Post by headlice on 2009-05-02
> **tjeremiah said:**
> Intel and Ubuntu dont seem to like each other. Ive had this problem since 8.10 with screen tearing and with 9.04, the problem is worst. Maybe this bug report I filled out can help? The more response to it, the faster I think it will get fixed.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359124](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359124)

8.10 worked great for video...

I will try the manual fix for it in a bit from the post below you and report back if it works or not.  I just prepared a USB drive for 8.10 if all else fails...

---

### Post by headlice on 2009-05-02
> **inobe said:**
> check out this pinned intel performance article, many have fixed performance issues.

read [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

SWEET!  This fixed the video problem.  Too bad my wifi is broke....

I am using a USB wifi adapter.  I am guessing the kernel that I installed does not support it out of the box.  Oh well- I have used ndiswrapper many times before- shouldnt be a problem here.

---

### Post by inobe on 2009-05-02
don't know about the wireless issue, you may want to start a topic in networking forum, i am certain someone knows the answers.

---

### Post by neekz on 2009-05-03
turning off normal visual effects fixed the problem for me.

 9.04 Jaunty, 64 bit flash pluggin - standered firefox, ati x1250

---

### Post by d_morgan on 2009-08-05
I just wanted to report the same problem and get my setup listed in case others have a similar situation and know of a fix.

Full screen flash playback (such as hulu) has also been choppy for me also since upgrading to 9.04.  It worked fine in ubuntu 8.10, firefox version I had (wish i kept the number).

  My workaround is to use the pop-out option in hulu and adjust the window size to be as big as possible before the chopping/jerking happens.

  My system is a Shuttle SG33G5 with intel G33 chipset.  I'm using the integrated graphics with the chipset, the intel GMA 3100.  Processor is a dual core something or other but since it worked on 8.10 processor speed isn't the problem.

  Software installed is ubuntu 9.04 all updates made as of jul-30th.  Firefox version is 3.0.12 with shockwave flash 10.0 r22 plug-in.

I see this reference another thread so i will try that next but it would be nice if ubuntu developers would include the fixes right in the regular release. [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by ntg on 2010-02-09
I seem to have the same problem with 9.10 . My Visual Effects are set to "None" and the problem seems to have to do with flash, since its not just the hulu site.

---

