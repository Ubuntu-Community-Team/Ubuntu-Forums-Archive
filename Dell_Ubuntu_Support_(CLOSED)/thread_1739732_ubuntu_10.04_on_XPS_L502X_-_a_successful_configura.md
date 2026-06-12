---
title: "ubuntu 10.04 on XPS L502X - a successful configuration"
date: 2011-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xinwu on 2011-04-26
Hi, everyone!

I just bought an XPS L502x, and installed ubuntu 10.04 on it. Everything works well, and I'd like to share my experience.

There are only two steps to make XPS and ubuntu work together!

1) install ubuntu 10.04. Nothing special.

2) due to the integrated intel graphic unit, we need drivers from intel. ([www.intellinuxgraphics.org](www.intellinuxgraphics.org)). For those of you, who merely need the binary, please check [https://edge.launchpad.net/~xorg-edgers](https://edge.launchpad.net/~xorg-edgers). Add this PPA to your sources.list and install the latest linux-image-x.x.x-x-generic and linux-headers-x.x.x-x-generic (I'm using 2.6.35-25). Reboot!

Confirmed working hardwares (those are enough for me):
1) screen resolution: 1366x768.
2) sound card: record and/or play.

unconfirmed hardware:
1) webcam (I don't use it).

Additional note - Optimus of nvidia:

1) I'm satisfied with the intel card, and I never play a 3-D game on Linux. So, forget it!

2) I need CUDA for my development. CUDA (toolkit 3.2) works, but behaves a little strange. In my case, if I run deviceQuery as a normal user first, cudaGetDeviceCount would fail. root, however, can run deviceQuery correctly. Then, after the execution as a root, normal user can run deviceQuery as well! It's magic!

I hope this helps the others!

More issues:

1) if you need suspend, those threads can help ([http://ubuntuforums.org/showthread.php?t=1634301](http://ubuntuforums.org/showthread.php?t=1634301))

---

### Post by deere on 2011-04-27
Hey,

Thanks for your post.
I'm planning to buy an XPS L502X (Core i7,  Nvidia GT540M) and want to use it with Ubuntu.
My questions would be:
- Does the HDMI work with the Intel driver, is the HDMI port detected?
- Do you have a FullHD screen which you can only use with 1366x768 resolution or a 1366x768 screen?

I'm interested because [here]("https://lists.launchpad.net/hybrid-graphics-linux/msg00701.html") someone says that the HDMI port works only with the Nvidia graphics card.

---

### Post by RI_VIPER on 2011-04-27
hi everyone!

I recently got a dell xps l502x and decided to get started with ubuntu. I am a total novice.


I installed the 10.10 version, but there seems to be a problem with the graphics card (nvidia gt 540m). I installed the recommended drivers that Ubuntu suggested, but I find it's not working, although it shows the driver is enabled. I can't turn on the visual effects. Also pressing (CTRL+ALT+F2) and then trying to return (CTRL+ALT+F7) results in a hung situation. 
After installing the driver I have done whatever the error message asked like reconfiguring and then restarting the X server, but without result. I even downloaded the drivers provided by nvidia, but still the same result.

Also the touch keys dont work, only the middle one (configurable in windows) reduces the brightness. How can I make them work?

Would installing the 11.04 release work? Please help. Thank you.

---

### Post by xinwu on 2011-04-28
Hi, deere!

I never tried the HDMI port, I don't know whether it works or not.

For the build-in monitor of the laptop, it would NOT work with 1366x768 after you finish the first normal installation. You need to install a newer kernel from the aforementioned PPA. Then 1366x768 works automatically and properly.

---

### Post by xinwu on 2011-04-28
Hi, ri_viper!

The version of the kernel is more important than the version of a ubuntu release. If some hardware doesn't work, upgrade the kernel and related modules is generally the first step.

Just try the two steps as I was writing. I chose 10.04 because it's LTS, and it has also been tested to be compatible with Intel Composer XE and CUDA toolkit 3.2. However, you are free to pick up any version of ubuntu.

Do NOT install the nvidia driver for your graphic card, unless you develop your applications by using CUDA! Due to the fxxking Optimus technology, the nvidia card will NEVER be used for the purpose of display on Linux, if the laptop has an integrated intel card. Therefore, you can safely ignore the nvidia official drivers completely in most cases.

If you have installed the nvidia driver, you might remember that in the very last step, you were asked to choose the 'xorg.conf' file from nvidia. Do NOT choose this configuration file from nvidia! This file can result in a black screen for the failure of xserver because the nvidia card could NOT be found (remember the nvidia card is not used for display on Linux). If you have this 'xorg.conf' file in /etc/X11 or some other directories, just delete it! It's useless! The newer versions of X can do everything automatically, the 'xorg.conf' file, hence, is no longer compulsive. If it exists, x would read the configurations. Otherwise, an automatic configuration will launch.

---

### Post by xinwu on 2011-04-28
Just a little question!

Does anyone know whether it is possible to buy a DELL laptop WITHOUT the pre-installed Windows? Because I don't want to waste 1) my money for a Windows license, and 2) my time for getting rid of it at the very beginning. I was a Mac user, but Apple now uses AMD cards, which do not support CUDA, so I switched to Linux. Anyway, both are UNIX-like.

---

### Post by Kai69 on 2011-04-28
> **xinwu said:**
> Just a little question!

Does anyone know whether it is possible to buy a DELL laptop WITHOUT the pre-installed Windows? Because I don't want to waste 1) my money for a Windows license, and 2) my time for getting rid of it at the very beginning. I was a Mac user, but Apple now uses AMD cards, which do not support CUDA, so I switched to Linux. Anyway, both are UNIX-like.


You can but you will need to call Dell directly, if you live in the US they still show ubuntu on their site 

_[http://www.dell.com/us/business/p/laptops#facets=80770~0~1791343&p=1](http://www.dell.com/us/business/p/laptops#facets=80770~0~1791343&p=1)_

---

### Post by xinwu on 2011-04-29
Kai69, thanks!

---

### Post by RI_VIPER on 2011-04-30
hi xinwu!

 thanks for the info. I have a few questions. how do I upgrade the kernel.
The ubuntu site recommends 32-bit download. I have a 64 bit machine. Which one should I go for and why? Also I have seen my friends computers which have no graphics cards and are relatively old machines show much better graphics than mine. during  the ubuntu startup my screen flickers while loading the login screen (not the whole screen) , the login image specifically, as if its loadind in parts, while it's so smooth in others. I have intel hd graphics 300 and nvidia gt540m 2gb. so even if nvidia's not working intel should.

---

### Post by Kai69 on 2011-05-01
RI_VIPER

If you want the 64bit OS on the Ubuntu site when it says 32bit click the box and it will show 64bit then you can download the 64bit OS 

As to you graphics problem have you installed the driver ?? got to System / Administration / Additional Drivers ,,, let it run and if there is a driver for your card then you can install it once that is installed then reboot and the graphics card  should now work properly.

---

### Post by Kai69 on 2011-05-01
RI_VIPER

If you want the 64bit OS on the Ubuntu site when it says 32bit click the box and it will show 64bit then you can download the 64bit OS 

As to the difference between 32/64bit OS, 32bit will only use max 3.4GB ram so if you have more installed you will need either the PAE kernal  ( install the pae kernal in Synaptic ) or 64bit OS ,
64bit OS will run faster opening/ closing programs and video playback is smoother 

As to you graphics problem have you installed the driver ?? got to System / Administration / Additional Drivers ,,, let it run and if there is a driver for your card then you can install it once that is installed then reboot and the graphics card  should now work properly.

---

### Post by cbarmpar on 2011-05-01
Dear xinwu,

Many thanks for your post.

I also have a similar system the XPS L702x unfortunately equipped with the optimus and not switchable through the BIOS hence cannot use the Nvidea driver!!!!

But my main concern is to be able to use CUDA.

Did you manage to use CUDA without installing the Nvidea driver?
If you install the nvidea driver does the system crashes?
How can I update my drivers for the integrated GPU(Intel)?

I am using the 11.04 version of ubuntu

Also the webcam of our system works out of the box.

Many thanks in advance.
Christos

---

### Post by xinwu on 2011-05-03
To RI_VIPER,

Do you know the command "apt-get"? If you know that, just switch to root and enter something like "apt-get install linux-image-x.x.x-x-generic and linux-headers-x.x.x-x-generic" in a terminal. Replace the characters of 'x' with appropriate numbers, please! If you have no idea about "apt-get", just google "debian package management" or "ubuntu package management" to learn some basics on "apt-get", "dpkg" and "apt-cache" etc.

Kernel is the most important part of an operating system. It connects the hardwares and many other programs. If you just want your computer work, the version of the kernel is crucial. Don't care too much about the release versions of the Linux distributions.

Please use 64 bit for obvious reasons, which are also difficult to be explained shortly in terms of "how computer works".

Maybe you need to re-install a clean 64 bit ubuntu for your laptop. Before doing so, please make sure that you can understand my first thread. I'm sorry, I didn't give the very detailed instructions step by step. Those steps are really basic. They should not be an obstacle for a general Linux user.

Good luck with the ubuntu on your L502x!

---

### Post by xinwu on 2011-05-03
to cbarmpar,

Because of the "optimus", the nvidia driver of the card is only useful for CUDA, but not for the purpose of display on the screen. If you need CUDA, then you need to install the nvidia driver for GPU.

What do you mean by saying "crash"? A black screen if you just enter "startx"? The current xserver can perform an automatic configuration, if "xorg.conf" is not present in an appropriate directory. If "xorg.conf" exists, xserver will, however, try to read the configurations. As far as I remember, the last step of installing nvidia driver would prompt you to use their "xorg.conf". Either "yes" or "no" works, and you exit the installation of the driver. If you choose "yes", however, then you have to remove the nvidia "xorg.conf" manually. Therefore, please choose "no" in the previous step. :)

Please read my first thread and the followings to find out how to make your integrated intel card work!

Good luck!

---

### Post by cbarmpar on 2011-05-03
Thanks for your response!

By crash I meant that the x server doesn't load anymore and I can only see the command prompt.

So in order to install cuda on my optimus laptop(dell xps L702x) I should write no when it prompts for X configuration.

Apart from that is there anything else that I need to do when installing the cuda various files?

Many thanks

---

### Post by dvirsky on 2011-05-04
Hi,
just a tip for anyone stuck without HDMI: this machine has a Mini DisplayPort socket, which is apparently governed by the intel card. this means that in order to get video out, just plug a mini DP to DVI/HDMI/VGA adapter to the socket, and connect your screen.

This will work without any further configurations.

---

### Post by xinwu on 2011-05-05
To cbarmpar,

Yes. "xorg.conf" from nvidia intends to use the discrete nvidia card, but that card is not for display. So you're back to the command line interface.

Please, say no, and forget the nvidia's xorg.conf.

An additional note. A CUDA application must be launched initially as a root, and then normal users can launch any CUDA applications. I don't know why is that.

---

### Post by secristrc on 2011-05-12
Can some one give me pointers on where to download what I need to make the 1366x768 video work on the L502X?  It isn't obvious to me what to download from [www.intellinuxgraphics.org](www.intellinuxgraphics.org) or using the PPA at [https://edge.launchpad.net/~xorg-edgers](https://edge.launchpad.net/~xorg-edgers).  The files linux-image-x.x.x-x-generic and linux-headers-x.x.x-x-generic and reference to 2.6.35-25 are kernels and not video drivers, right?

Nonetheless I am heartened by this post and looking forward to getting everything working.

Thanks!
rcs

---

### Post by xinwu on 2011-05-16
Right! It's the kernel. But this kernel comes with many compiled modules, which can drive your hardwares. Don't worry about the detailed. just install those packages and reboot your system.

---

### Post by secristrc on 2011-05-17
Thanks for response.  I was confused about the URLs which are not germane any longer.  Instead from Synaptic I simply added:

linux-image-2.6.35-28-generic      and
linux-headers-2.6.35-28-generic

and 1366x768 became the new default, and it looks great!

Using this kernel the **webcam works** if you install Cheese.

**Flash 10 works** with the 64-bit if you download the ["square" beta]("http://labs.adobe.com/technologies/flashplayer10/square/") and copy the libflashplayer.so file to your browser plugin directory (e.g. /usr/lib/firefox-3.6.17/plugins).

Thanks again!
rcs

---

### Post by Dmeni on 2011-05-26
Has anyone experienced Cuda on matlab on this laptop? I'm running matlab under ubuntu 11.04 and after installing all the drivers the card is still undetected :(

On the workstation at my lab I've had the same issues described in this forum I run matlab as user and CUDA was not available but after running it as root it was fine. On dell xps l502x the problem remains ...

Any suggestions?

---

