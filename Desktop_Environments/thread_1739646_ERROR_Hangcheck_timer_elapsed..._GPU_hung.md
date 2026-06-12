---
title: "*ERROR* Hangcheck timer elapsed... GPU hung"
date: 2011-04-26
forum: Desktop Environments
---

### Post by cccc on 2011-04-26
hi

I have Lucid Lynx with Kernel 2.6.32 and after 10-20 min working the Gnome Desktop freezes.

I have these messages in /var/log/syslog:

[B][COLOR="Red"][drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
  render error detected, EIR: 0x00000000
 [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 3115 at 3114)[/COLOR][/B]

My video card:```

description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
```
```

# lsmod | grep video
video                  14605  1 i915
output                  1204  1 video
thermal_sys             9378  3 video,processor,thermal

```

Howto solve this problem?

---

### Post by cccc on 2011-04-30
I've done the Kernal upgrade to 2.6.38-2-686, but still doesn't help.

---

### Post by cyberbuff on 2011-06-03
I am having the same issues with 11.04. Kernel updated to 2.6.39.0. No dice. :-/

---

### Post by cccc on 2011-06-07
SOLVED in Debian!

**[COLOR="Red"]On the end I changed from Ubuntu to Debian Squeeze[/COLOR]**, but I had exact the same problem.


Installing these debian wheezy packages on squeeze solved my problem:```

# dpkg -l |grep xserver-xorg-video-intel
ii  xserver-xorg-video-intel             2:2.15.0-3                        X.Org X server -- Intel i8xx, i9xx display driver

# dpkg -l |grep libdrm-intel1
ii  libdrm-intel1                        2.4.25-2                          Userspace interface to intel-specific kernel DRM services -- runtime
```
You can try after making an image (backup) of your ubuntu system, to add these wheezy repos 
in /etc/apt/sources.list:```

deb http://ftp.ch.debian.org/debian/ wheezy main contrib non-free
deb-src http://ftp.de.debian.org/pub/debian/ wheezy main contrib non-free
``` and install:```

# apt-get update
# apt-get install xserver-xorg-video-intel libdrm-intel1
```

BTW pls let know if helps.

---

### Post by cyberbuff on 2011-06-08
Thanks. I just removed compiz-core and compiz-plugins. That worked. Since I not much into cool graphics, Compiz was of no use, anyway.

---

### Post by cccc on 2011-06-09
> **cyberbuff said:**
> Thanks. I just removed compiz-core and compiz-plugins. That worked. Since I not much into cool graphics, Compiz was of no use, anyway.

BTW have you installed xserver-xorg-video-intel and libdrm-intel1?

---

### Post by cccc on 2011-06-09
Another possible solution for the **82845G** video driver problem:

1.) create /etc/X11/xorg.conf```

# Xorg -configure
# cp /root/xorg.conf.new /etc/X11/xorg.conf
``` 

2.) put the following in /etc/X11/xorg.conf in Section "Device":```

Section "Device"
Identifier "Card0"
Driver "intel"
**Option "Shadow" "true"**
**Option "DRI" "false"**
**BoardName "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"**
BusID "PCI:0:2:0"
EndSection
```

Run "lspci | grep VGA" to find out the "BusID" and the "BoardName", for example:```

# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

BTW for additional information run the "lspci -v" command.

---

### Post by oldmankit on 2011-09-27
> **cccc said:**
> On the end I changed from ubuntu to debian, but I had the same problems.

**That's a problem of intel driver and not the kernel.**

Installing these debian wheezy packages on squeeze solved my problem:```

# dpkg -l |grep xserver-xorg-video-intel
ii  xserver-xorg-video-intel             2:2.15.0-3                        X.Org X server -- Intel i8xx, i9xx display driver

# dpkg -l |grep libdrm-intel1
ii  libdrm-intel1                        2.4.25-2                          Userspace interface to intel-specific kernel DRM services -- runtime
```
You can try after making an image (backup) of your ubuntu system, to add these wheezy repos 
in /etc/apt/sources.list:```

deb http://ftp.ch.debian.org/debian/ wheezy main contrib non-free
deb-src http://ftp.de.debian.org/pub/debian/ wheezy main contrib non-free
``` and install:```

# apt-get update
# apt-get install xserver-xorg-video-intel libdrm-intel1
```

BTW pls let know if helps.
Is this solution for Ubuntu or Debian?

---

### Post by cccc on 2011-10-07
> **oldmankit said:**
> Is this solution for Ubuntu or Debian?

It should work on both systems, pls try and let know if helps.

---

### Post by oldmankit on 2011-10-09
What fixed it for me was:
```
sudo  add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo  apt-get update
sudo apt-get upgrade
```

---

### Post by BlakJakNZ on 2012-02-06
Get this GPU error on my Lenovo Thinkpad T510 (i915 chipset) too.
Using the instructions on this forum I opted to add the ppa.

When I ran the upgrade some other stuff came in too, but the video-related packages that were changed were as follows:

(from /var/log/apt/history.log)

Start-Date: 2012-02-05  19:21:50
Commandline: apt-get upgrade
Upgrade: xserver-xorg-video-ati:amd64 (6.13.1-1ubuntu5, 6.13.2-0ubuntu1~xup1), libdrm-nouveau1:amd64 (2.4.21-1ubuntu2.1, 2.4.22-2ubuntu1), intel-gpu-tools:amd64 (1.0.2+git20100324-0ubuntu1, 1.0.2+git20100830+c935c60-0ubuntu0sarvatt), thunderbird-locale-en-us:amd64 (9.0+build2-0ubuntu0.10.10.1~mts1, 10.0+build1-0ubuntu0.10.10.1~mts1), libdrm-radeon1:amd64 (2.4.21-1ubuntu2.1, 2.4.22-2ubuntu1), thunderbird:amd64 (9.0+build2-0ubuntu0.10.10.1~mts1, 10.0+build1-0ubuntu0.10.10.1~mts1), nvidia-current-modaliases:amd64 (260.19.06-0ubuntu1, 290.10-0ubuntu1~maverick~xup1), xserver-xorg-video-intel:amd64 (2.12.0-1ubuntu5.2, 2.13.901-2ubuntu2~xup~maverick), libdrm2:amd64 (2.4.21-1ubuntu2.1, 2.4.22-2ubuntu1), libdrm-intel1:amd64 (2.4.21-1ubuntu2.1, 2.4.22-2ubuntu1), fglrx-modaliases:amd64 (8.780-0ubuntu2, 8.801-0ubuntu1~xup~maverick), thunderbird-gnome-support:amd64 (9.0+build2-0ubuntu0.10.10.1~mts1, 10.0+build1-0ubuntu0.10.10.1~mts1), xserver-xorg-video-radeon:amd64 (6.13.1-1ubuntu5, 6.13.2-0ubuntu1~xup1), thunderbird-locale-en:amd64 (9.0+build2-0ubuntu0.10.10.1~mts1, 10.0+build1-0ubuntu0.10.10.1~mts1)
End-Date: 2012-02-05  19:22:44

I returned to the office this morning and connected up my external monitor. I noticed that all was fine until I logged in, and my video settings reset themselves up for my 24" LCD Primary Monitor and the onboard secondary; the right hand inch or so of the LCD was blank, with the right most ~1cm showing the same picture as the left hand ~1cm of the primary screen.  Oh and the UI was mismatched with the display by about 1 inch (so I had to click to the right of where I wanted to be).

I did some searching and discovered I could backgrade packages by specifying versions, so I disabled the ppa and ran the following:

Start-Date: 2012-02-07  10:13:46
Commandline: apt-get install intel-gpu-tools=1.0.2+git20100324-0ubuntu1 xserver-xorg-video-intel=2:2.12.0-1ubuntu5.2
Downgrade: intel-gpu-tools:amd64 (1.0.2+git20100830+c935c60-0ubuntu0sarvatt, 1.0.2+git20100324-0ubuntu1), xserver-xorg-video-intel:amd64 (2.13.901-2ubuntu2~xup~maverick, 2.12.0-1ubuntu5.2)
End-Date: 2012-02-07  10:14:03

Things now appear to be working, having only backgraded intel-gpu-tools and xserver-xorg-video-intel.  

No idea if i'll still have the original bug - will no doubt find out in due course (when I try to resume my session and am forced to reboot from a terminal, if not cold-start ...

I'm still running Maverick but as this goes out of support in a couple of months I may wind up doing a dist-upgrade soon which may change the picture - though i'm not looking forward to going to Unity :( (yes, i'm averse to change...)

---

### Post by cccc on 2012-02-06
> **oldmankit said:**
> What fixed it for me was:
```
sudo  add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo  apt-get update
sudo apt-get upgrade
```

Which graphic card do you have?

---

### Post by cccc on 2012-03-04
Other solution is to upgrade Ubuntu version.
Kernel version 3.x.x should solve this problem.
This problem happens to Intel motherboards with Linux kernel 2.x.x which causes GPU to hung.

---

### Post by uteck on 2012-04-17
I am running 10.04 with the 3.0.0.17 backported kernel and it worked on some systems with this chipset (82845G/GL[Brookdale-G]/GE used in Dell GX60), but not others.  
The system is running XFCE and auto starts rdesktop in fullscreen, so it is just a gloried thin-client.  People are not using anything else on the system.

 Current xorg.conf 
```
Section "Device"
        Option     "DRI"                        "off"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
EndSection

Section "ServerFlags"
        Option "DontVTSwitch" "true"
EndSection

```

Modprobe.d for i915
```
options i915 modeset=1
```

I will try adding Option "Shadow" "true"  and see if that helps.

---

### Post by cccc on 2012-04-17
Pls try this in xorg.conf:```

Section "Device"
Identifier "Card0"
Driver "intel"
[B]Option "Shadow" "true"
Option "DRI" "false"[/B]
BoardName "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"
BusID "PCI:0:2:0"
EndSection
```

---

### Post by uteck on 2012-04-17
> **cccc said:**
> Pls try this in xorg.conf:```

Section "Device"
Identifier "Card0"
Driver "intel"
[B]Option "Shadow" "true"
Option "DRI" "false"[/B]
BoardName "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"
BusID "PCI:0:2:0"
EndSection
```

Still crashes with these options for me, about 3 times while typing this response, but it has been running fine for over 10 minutes now.

Currently I am using the above X.org settings along with "options i915 modeset=1" in /etc/modeprobe.d/i915.conf.  Without i915.conf resizing the desktop to 1024x768 does not work, and yes it has to be that size for the users with bad eyes.  The W2k systems I am replacing were running at 800x600!

Other systems running what I posted before will run for many hours or days without errors.  These crashes are just so random, but at least with the new kernel the interval is longer.

---

### Post by cccc on 2012-04-17
> **uteck said:**
> Still crashes with these options for me, about 3 times while typing this response, but it has been running fine for over 10 minutes now.

Currently I am using the above X.org settings along with "options i915 modeset=1" in /etc/modeprobe.d/i915.conf.  Without i915.conf resizing the desktop to 1024x768 does not work, and yes it has to be that size for the users with bad eyes.  The W2k systems I am replacing were running at 800x600!

Other systems running what I posted before will run for many hours or days without errors.  These crashes are just so random, but at least with the new kernel the interval is longer.

**[COLOR="Red"]Pls try to not use "i915 modeset=1[/COLOR]"** options and try to set a fix 1024x768 resolution in xorg.conf.

BTW have you done all online updates and is it possible to update the kernel to the newer one than 3.0.0.17?

Even you can try to update these packages: 

[B]xserver-xorg-video-intel 
libdrm-intel1
xorg
[/B]
from the backports, or debian wheezy packages.

---

### Post by uteck on 2012-04-17
> **cccc said:**
> Pls try to not use "i915 modeset=1" options and try to set a fix 1024x768 resolution in xorg.conf.

BTW have you done all online updates and is it possible to update the kernel to the newer one than 3.0.0.17?

Even you can try to update these packages: 

[B]xserver-xorg-video-intel 
libdrm-intel1
xorg
[/B]
from the backports, or debian wheezy packages.

Backports does not have anything newer, just the 3.0.0.17 kernel, and I would rather not install stuff from wheezy since that will make latter support a problem.

I will try setting the resolution in xorg.conf. 
Using "xrandr -s 1024x768" in /etc/profile works fine for other systems without this chipset. I hope that is the problem as I am running out ideas.

---

### Post by cccc on 2012-04-17
Yep, try this, but what kind of thin client is it, is it self-made?

---

### Post by uteck on 2012-04-17
> **cccc said:**
> Yep, try this, but what kind of thin client is it, is it self-made?
Yes, converting a bunch of old Dells, GX50,60,745 into thin clients.  Only the GX60 is having issues.  Latest attempt failed after 50 minutes. Removed the i915 from modprobe.d, ran update-initramfs.  Removed xrandr from /etc/profile, using this xorg.conf with standard 10.04 except for 3.0 kernel from backports.: 
```
Section "Device"
        Identifier "Card0"
        Driver "intel"
        Option "Shadow" "true"
        Option "DRI" "false"
        BoardName "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
EndSection

Section "ServerFlags"
        Option "DontVTSwitch" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device        "Device"
        Monitor       "Configured Monitor"
        DefaultDepth  24
        SubSection "Display"
                Depth          24
                Modes         "1024x768"   "800x600"
        EndSubSection
EndSection
```

But another GX60 has been running most of the day with all my tweaks.  I am starting to think that maybe this one system just has a mobo that is going bad.

---

### Post by cccc on 2012-04-17
> **uteck said:**
> Yes, converting a bunch of old Dells, GX50,60,745 into thin clients.  Only the GX60 is having issues.  

Which thin client is it exactly, can you pls give some more details?
Is it just one GX60 or more having this issue?

---

### Post by uteck on 2012-04-17
> **cccc said:**
> Which thin client is it exactly, can you pls give some more details?
Is it just one GX60 or more having this issue?
Multipal GX60 have been giving me issues, but so far there is one that is crashing every 45-50 minutes.  Others seem to stay up for days.  They are in remote locations, and I finally got one to test on locally an hour ago.

---

### Post by cccc on 2012-04-17
> **uteck said:**
> Multipal GX60 have been giving me issues, but so far there is one that is crashing every 45-50 minutes.  Others seem to stay up for days.  They are in remote locations, and I finally got one to test on locally an hour ago.

It's quite difficult to help, I still don't know what kind of thin client is it installed on GX60.
If just one machine is crashing, it's maybe a hardware problem.

BTW other solution is to install other graphic card than 82845G.

---

### Post by uteck on 2012-04-18
I reconfigured a few more GX60's to use only the xorg.conf file and removed the modprobe.d option.  One ran for a few hours then got the same error and crashed, but the other is running fine.  The one from yesterday which I thought had bad hardware and was crashing every hour is running fine today. 

Installing a new graphics card is not an option.  We are using 8-10 year old hardware for a reason.

The "thin-client" as I call it just stripped down XFCE that autostarts rdeskop and connects to a Windows server.  The end users should only see the Windows login screen once the system boots.

---

### Post by cccc on 2012-04-18
Try to put the following in /etc/X11/xorg.conf:```
 
Section "Device"
  Identifier "Card0"
  Driver "intel"
  Option "Shadow" "true"
  Option "DRI" "false"
  BoardName "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"
  BusID "PCI:0:2:0"
EndSection
```
 
Run "lspci | grep VGA" to find out the "BusID" and the "BoardName", for example:

# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE
Chipset Integrated Graphics Device (rev 01)

---

### Post by uteck on 2012-04-18
I got the same results as you;
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```
I don't have the BusID in the xorg.conf, but does that really matter?  From the X log file it is detecting the correct BusID and of the 2 systems I am monitoring now one has not crashed at all, and the other once.  I am not monitoring the one from yesterday since I don't trust the hardware on that unit.

---

### Post by cccc on 2012-04-18
**This Bug is very tricky and not really solved in your Ubuntu version.** 
You'll find a lot unsolved bug reports about this problem. 
You can work hours or days, without having this problem and suddenly you get it.
Last year, I've really spent some weeks trying to fix this problem. 
That was the reason, why I'm finally switching to Debian. 
I'm using squeeze, patched with some wheezy packages, or just wheezy for all machines with 82845G.

My all thin clients, based on patched squeeze or wheezy work very stable with 82845G and don't get any problems, since one year.

You can try to upgrade your ubuntu version to the newer one, or try Debian, not much difference from Ubuntu.
Any other solution seems to be at the moment wasting of time. 

Anyway good luck!

---

### Post by uteck on 2012-04-19
> **cccc said:**
> **This Bug is very tricky and not really solved in your Ubuntu version.** 
You'll find a lot unsolved bug reports about this problem. 
You can work hours or days, without having this problem and suddenly you get it.
Last year, I've really spent some weeks trying to fix this problem. 
That was the reason, why I'm finally switching to Debian. 
I'm using squeeze, patched with some wheezy packages, or just wheezy for all machines with 82845G.

My all thin clients, based on patched squeeze or wheezy work very stable with 82845G and don't get any problems, since one year.

You can try to upgrade your ubuntu version to the newer one, or try Debian, not much difference from Ubuntu.
Any other solution seems to be at the moment wasting of time. 

Anyway good luck!

Thanks for the help.  I guess we will just have to put up with the GX60's crashing randomly since I can't use Debian packages because of the patching solution management choose (don't ask, only management can decide on something this stupid).  I hope we get new hardware by next year when support for 10.4 ends.

I did change to using just the 3.0 kernel and your xorg.conf, sans DbusID, and it is working well on 2 machines so I can at least close out that ticket.

Is there an open bug report for this with Ubuntu?  I think I saw one on a previous Google search.
Never mind, found it again, Bug #554835 is still open.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/554835](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/554835)

---

### Post by cccc on 2012-04-19
You're welcome!
There is no final solution for this BUG, except upgrade Ubuntu version, you can check in div. bug reports:

[http://www.google.com/#hl=en&sclient=psy-ab&q=ubuntu+bug+ERROR+Hangcheck+timer+elapsed&oq=ubuntu+bug+ERROR+Hangcheck+timer+elapsed&aq=f&aqi=&aql=&gs_nf=1&gs_l=hp.3...2260.2260.2.2454.1.1.0.0.0.0.82.82.1.1.0.PLR7hezgwO8&psj=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=f5cad1b8863da9dc&biw=1024&bih=600](http://www.google.com/#hl=en&sclient=psy-ab&q=ubuntu+bug+ERROR+Hangcheck+timer+elapsed&oq=ubuntu+bug+ERROR+Hangcheck+timer+elapsed&aq=f&aqi=&aql=&gs_nf=1&gs_l=hp.3...2260.2260.2.2454.1.1.0.0.0.0.82.82.1.1.0.PLR7hezgwO8&psj=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=f5cad1b8863da9dc&biw=1024&bih=600)

Some people reporting have solved, others if they are trying the same solution not etc.
BTW some bugs they are closing with the message: it was solved in a newer version.

---

### Post by uteck on 2012-04-19
Everytime I give up I have to try one more thing.
i915-kms.conf is back but using modeset=0
and xorg.conf is using fbdev driver
So far seems okay on my test box and on a users system that was crashing.

Probably not the best solution for someone that wants to use the desktop, but since I only care about rdesktop this might work.

---

### Post by uteck on 2012-04-19
fbdev just gives a blank screen so switching back to intel driver with options i915 modeset=0.  
If this does not work we might just have to convert the GX60 back to Windows, but I think we might be able to get XP on them and not Win2k.

---

### Post by cccc on 2012-04-20
> **uteck said:**
> fbdev just gives a blank screen so switching back to intel driver with options i915 modeset=0.  
If this does not work we might just have to convert the GX60 back to Windows, but I think we might be able to get XP on them and not Win2k.

Normally, you should use **intel driver** and you don't need i915 modeset=0 option.
Anyway, if still crashing go back to Windows XP, Win2k, depends of RAM and virus scanner or try Debian (patched with some wheezy packages) or wheezy.
Better than XP, Win2k is Windows Embedded Standard 2009 as a thin client, but it costs a lot of money. 
We're using Debian successfully on more than 500 workstations and is not crashing.

I'll create soon debian, running as a thin client from USB directly with rdesktop, citrix and vmware-view client and you don't need a hard disk, but I'm still working on it.

---

### Post by nbd on 2012-05-08
Same thing happening, Ubuntu Studio 12.04, intel driver 2:2.17.0-1ubuntu4

I'm going to try the x-swat update, which is 2.19 

I have also experienced total shutdowns, and in those cases nothing in the logs, computer just suddenly shuts down like plugging out the power cord.

---

### Post by RJARRRPCGP on 2012-05-08
> **nbd said:**
> 

I have also experienced total shutdowns, and in those cases nothing in the logs, computer just suddenly shuts down like plugging out the power cord.

Probably dying battery or too high of core temps.

---

### Post by uteck on 2012-05-26
I installed 12.04 on my test box with no special settings and so far the Intel driver works fine.  I'll let it burn-in over the weekend and then stress test it a bit more, but from the few hours I spent with it on Friday it worked fine.

Now that I am almost done deploying to 3000 workstations I may have to start over and reimage them with 12.04, but I would have to do that before next April anyway when 10.04 support ends, so at least I get plety of time now to test before deploying.

---

### Post by cccc on 2012-05-27
> **uteck said:**
> I installed 12.04 on my test box with no special settings and so far the Intel driver works fine.  I'll let it burn-in over the weekend and then stress test it a bit more, but from the few hours I spent with it on Friday it worked fine.

Now that I am almost done deploying to 3000 workstations I may have to start over and reimage them with 12.04, but I would have to do that before next April anyway when 10.04 support ends, so at least I get plety of time now to test before deploying.

Ubuntu 12.04 uses a newer kernel and its kernel shouldn't produce this error with 82845G/GL graphic card:
 **ERROR* Hangcheck timer elapsed... GPU hung.*

---

### Post by h3n5y on 2012-12-13
Got the same error on a Thinkpad R61:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)


syslog:

Dec 13 17:19:11 srv95 kernel: [106179.032075] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:19:11 srv95 kernel: [106179.032088] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Dec 13 17:19:11 srv95 kernel: [106179.034029] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 11743847 at 11743618, next 11744261)
Dec 13 17:19:11 srv95 kernel: [106179.100071] [drm:init_ring_common] *ERROR* render ring initialization failed ctl 00000000 head 00000000 tail 00000000 start 00000000
Dec 13 17:19:11 srv95 kernel: [106179.100566] ------------[ cut here ]------------
Dec 13 17:19:11 srv95 kernel: [106179.100609] WARNING: at /build/buildd/linux-3.2.0/drivers/gpu/drm/i915/intel_display.c:793 intel_enable_pipe+0x14a/0x150 [i915]()
Dec 13 17:19:11 srv95 kernel: [106179.100612] Hardware name: 8943A21
Dec 13 17:19:11 srv95 kernel: [106179.100614] PLL state assertion failure (expected on, current off)
Dec 13 17:19:11 srv95 kernel: [106179.100616] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat uvcvideo videodev v4l2_compat_ioctl32 snd_usb_audio snd_usbmidi_lib uas usb_storage pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) dm_crypt kvm_intel kvm joydev rfcomm parport_pc bnep ppdev bluetooth snd_hda_codec_analog binfmt_misc nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc arc4 pcmcia snd_hda_intel snd_hda_codec iwl3945 snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi snd_seq_midi_event iwl_legacy yenta_socket pcmcia_rsrc mac80211 serio_raw pcmcia_core snd_seq cfg80211 thinkpad_acpi nvram snd_timer snd_seq_device snd soundcore snd_page_alloc mac_hid lp parport usbhid hid firewire_ohci firewire_core crc_itu_t tg3 i915 drm_kms_helper drm i2c_algo_bit video
Dec 13 17:19:11 srv95 kernel: [106179.100666] Pid: 29634, comm: kworker/u:0 Tainted: G           O 3.2.0-34-generic #53-Ubuntu
Dec 13 17:19:11 srv95 kernel: [106179.100669] Call Trace:
Dec 13 17:19:11 srv95 kernel: [106179.100678]  [<ffffffff81066f0f>] warn_slowpath_common+0x7f/0xc0

---

### Post by cccc on 2012-12-13
> **h3n5y said:**
> Got the same error on a Thinkpad R61:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)




Which Ubuntu and which kernel have you installed?

---

### Post by h3n5y on 2012-12-13
> **cccc said:**
> Which Ubuntu and which kernel have you installed?

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

Linux srv95 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:48:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


Thanks,
henry

---

