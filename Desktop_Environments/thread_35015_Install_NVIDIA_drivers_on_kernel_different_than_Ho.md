---
title: "Install NVIDIA drivers on kernel different than Hoary 2.6.10.5"
date: 2005-05-17
forum: Desktop Environments
---

### Post by Chareos on 2005-05-17
Hi all,


I'm going crazy.
If I install an Ubuntu kernel (2.6.11.x for example) there is no way I can reinstall NVIDIA DRIVERS ! These bind always to Hoary 2.6.10.5 !

If I recompile mine from kernel.org I can install NVIDIA.com drivers, but after a couple of reboot I get undefined symbol at startx (missing keyboard, he says) unless I reinstall drivers again.


I *must* use a 2.6.11.8 kernel or later because they fix a problem on my videocard.
So, please, PLEASE help me. I'm struck with a wonderful,fully working OS - less than for a thing I did a thousand of times in slackware: recompile a damn kernel and install those damn nvidia drivers !

---

### Post by tread on 2005-05-17
I seem to remember reading:
Hoary - official kernel 2.6.10 - restricted modules to be released just for this version.
For latest restricted, wait for Breezy ... which means you will have to compile the kernel sources yourself.

Maybe someone who knows the restricted modules status better could jump in at this point.

---

### Post by neighborlee on 2005-05-17
[QUOTE=Chareos]Hi all,


I'm going crazy.
If I install an Ubuntu kernel (2.6.11.x for example) there is no way I can reinstall NVIDIA DRIVERS ! These bind always to Hoary 2.6.10.5 !

If I recompile mine from kernel.org I can install NVIDIA.com drivers, but after a couple of reboot I get undefined symbol at startx (missing keyboard, he says) unless I reinstall drivers again.


I *must* use a 2.6.11.8 kernel or later because they fix a problem on my videocard.
So, please, PLEASE help me. I'm struck with a wonderful,fully working OS - less than for a thing I did a thousand of times in slackware: recompile a damn kernel and install those damn nvidia drivers ![/QUOTE]
--------------
I also have these problems...today I downloaded ( because I heard that was how to fix the weird gnome desktop crashes ive been seeing and that MaNY others have ) the nvidia driver from their site and did telinit 1 ( although the compiling gives errors about it being wrong 'level', - and frankly what init level actually does work in debian to avoid this, whereas in redhat telinit '3' does the job nicely with no nviida errors dudring compile so I WISH all distros would agree to a standard here !!) , and even though I got errors saying telinit 1 might cause erors..I never got any during the ./NV*.run session..so I then do: startx < and saw nvidia logo and gdm starting and I got into desktop fine..

I then restart the company and find that not even gdm will not load ( and the nvidia  logo which tries to display only gives a black screen ).

if I do ./NV*.run again ..and then startx..things go smoothy..w-t-h is going on here ?.

Im' not sure how much more time I can devote to this problem..sure I can use the canned synaptic drivers but then im' back to a unstable system ( if you believe the forum posts)..

so i'm mass confused by now and  HOPE someone enlightened out here knows what is going on here..;-)

cheers
neighborlee

---

### Post by Chareos on 2005-05-17
I'd just LOVE to be able to install nvidia drivers... and have things working.

---

### Post by Chareos on 2005-05-18
So, I must think there is NO Ubuntu user with custom compiled kernel AND nvidia drivers installed and working ?

---

### Post by SNo0py on 2005-05-18
[QUOTE=Chareos]So, I must think there is NO Ubuntu user with custom compiled kernel AND nvidia drivers installed and working ?[/QUOTE]
Hm... I don't think so, but it is definitely the case, that there are not a lot of users who are compiling the Kernel by themselfes.

For example: I'm currently in the progress of switching from Gentoo to Ubuntu. Why? Because after 3 years Gentoo I hate to compile stuff :) And I was searching an easy-to-use Desktop-based Linux which can be updated easily (and fast)... And Ubuntu offers me exactly that. No need to compile applications or the kernel. No need to wait 20 hours to have the system installed (not: up and running! A lot of stuff needs to be configured afterwards...).
Don't get me wrong here - Gentoo is great! Portage is reall great! But I don't have the time and mood to compile every single programm and to hack around 3 hours for every singe update...
You might ask: Debian? Too old. The stable packages are really old compared to Gentoo... 
And why Ubuntu? Yeah, it's somehow in the middle - a new release every 6 month (which is fine), up-to-date software (which is fine), fast & easy updates (which is fine).... so for me the best of two worlds.

So, that's the reason why there are not a lot of Ubuntu-users who compile the kernel by themselfes...

---

### Post by Chareos on 2005-05-18
I agree, and very happy with Ubuntu. I've been on Slackware since a year and on Gentoo for 2 weeks. I'd NOT leave Ubuntu as of now...

But there MUST be a way to tinker things a bit, and make at least things working with a custom kernel. Or have totem read video files with mp3 streams. Or have Mplayer read AC3 streams. And so on...


I can't get satisfied, after all    :) 


So, once again ... nobody managed to compile his own kernel and have nvidia drivers working... and stay there after a couple of reboots ?

---

### Post by nikopol on 2005-05-20
[QUOTE=Chareos]So, once again ... nobody managed to compile his own kernel and have nvidia drivers working... and stay there after a couple of reboots ?[/QUOTE]

Well I haven't and I've fiddled about as much I could to get it working so I've given up and just reinstall the NVidia drivers on each reboot. I'm not sure if we can file this as a bug since the drivers are third-party. 

If anyone wants a look at the  logs I can post them here.

---

### Post by skoal on 2005-05-20
skoal@morpheus://~ $ uname -a
Linux morpheus 2.6.11-1-686 #1 Fri Feb 11 15:59:02 UTC 2005 i686 GNU/Linux
skoal@morpheus://~ $ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)

* I think I just recompiled the NVIDIA driver after fetching the 2.6.11 headers.  I think I ran apt-get install nvidia-glx afterwards.  It's been awhile so I don't recall the steps. 

skoal@morpheus://~ $ modinfo nvidia
filename:       /lib/modules/2.6.11-1-686/kernel/drivers/video/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
parmtype:       nv_disable_pat:int
parmtype:       NVreg_VideoMemoryTypeOverride:int
parmtype:       NVreg_EnableVia4x:int
parmtype:       NVreg_EnableALiAGP:int
parmtype:       NVreg_ReqAGPRate:int
parmtype:       NVreg_NvAGP:int
parmtype:       NVreg_EnableAGPSBA:int
parmtype:       NVreg_EnableAGPFW:int
parmtype:       NVreg_SoftEDIDs:int
parmtype:       NVreg_Mobile:int
parmtype:       NVreg_ResmanDebugLevel:int
parmtype:       NVreg_FlatPanelMode:int
parmtype:       NVreg_DevicesConnected:int
parmtype:       NVreg_VideoEnhancement:int
parmtype:       NVreg_RmLogonRC:int
vermagic:       2.6.11-1-686 preempt 686 gcc-3.3
depends:        agpgart
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*

/edit I thought you just needed the latest NVIDIA driver working on 2.6.11 with the no-reboot issue.  If it's just the custom kernel build giving you problems, I'd recompile NVIDIA drivers then re-run apt-get install nvidia-glx like I did for the stock 2.6.11 kernel.

---

### Post by nikopol on 2005-05-20
I need a patched kernel to get my Nova-T card running. Here's my output:

```
mambo@ubuntu:~$ uname -a
Linux ubuntu 2.6.10.ck001 #1 Mon May 9 15:48:29 BST 2005 i686 GNU/Linux
mambo@ubuntu:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
GCC version:  gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
mambo@ubuntu:~$ modinfo nvidia
filename:       /lib/modules/2.6.10.ck001/kernel/drivers/video/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
vermagic:       2.6.10.ck001 preempt 386 gcc-3.3
depends:        agpgart
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
```

---

### Post by Chareos on 2005-05-26
[QUOTE=skoal]I thought you just needed the latest NVIDIA driver working on 2.6.11 with the no-reboot issue.  If it's just the custom kernel build giving you problems, I'd recompile NVIDIA drivers then re-run apt-get install nvidia-glx like I did for the stock 2.6.11 kernel.[/QUOTE]


I did exactly this thing 2 days ago and testing... it worked like a charm; I'd to change xorg.conf and modify corekeyboard and corepointer as like as in ubuntu xorg.conf

Then I came here to tell everybody how I solved... and read your post.

First of all, Thank you.
Second... ppl, skoal is right :)

---

