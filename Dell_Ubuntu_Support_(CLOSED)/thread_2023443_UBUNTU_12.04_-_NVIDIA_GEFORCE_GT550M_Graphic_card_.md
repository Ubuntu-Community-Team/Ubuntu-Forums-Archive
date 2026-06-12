---
title: "UBUNTU 12.04 - NVIDIA GEFORCE GT550M Graphic card does driver not working"
date: 2012-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nick78 on 2012-07-12
Hi, 
I need your help, I just installed Ubuntu 12.04 on my XPS 17 and seems it does not recognize the graphic card.  I use an application called sysinfo to check my system information and when I click on the graphic card I can see this screen:



System details:

XPS L702X - i7-2670QM
XPS 72x BTS: 2nd generation Intel Core i7 - 267QM proc 2.20 GHz with Turbo
Display: 17.3in HD + WLED True-Life (1600 x 900) with 2.0 Mega Pixel Integrated
Memory: 6GB (1 x 4GB + 1 x 2GB 1333MHz DDR3 Dual Channel
Graphics: 1GB NVIDIA GeForce GT 550M Graphics Card



Does anybody have the same problem? 

Thanks
Nico

---

### Post by tenmoi on 2012-07-12
Install bumblebee.

Google 'how to install bumblebee on ubuntu 12.04' and install it and keep your fingers crossed.

---

### Post by OM55 on 2012-07-13
Nvidia is known to have a tricky (i.e. fragile) support under Ubuntu. Sometimes it works out of the box while other times a lot of tweaking is required. Sadly the proprietary video driver from Nvidia is not always stable and definitely doesn't provide 100% support to all their different video cards.

The good news is that the open source Nvidia driver is pretty good and unless you want to play high octan 3D computer games - it will work just fine for everything else.

Based on your description it sounds like the Ubuntu installer was trying to automatically install the Nvidia proprietary driver (this is the default setting), but that driver is not working properly with your video card, so you have only the basic support without the bells and whistles. 

I had this issue recently and the following steps resolved the problem in my case:

First, try to update the NVidia driver to the latest version:
```
sudo apt-get install nvidia-current
```Then do a full restart to make sure the video hardware gets a full reset before being accessed by the new driver.

If that didn't help, try to remove it back (you can also do it from the Software Center):
```
sudo apt-get remove nvidia-current
```(I specifically did not do any purge or autoclean). What happens is that the installation of nvidia-current driver may add any missing libraries or settings that the Ubuntu installation did not have or had a problem with.
Once it is removed, it is only removing the nvidia-current driver but leaving the rest of the stuff and setting, if any were made. So the system will simply revert to the open source driver - which should work.

After another restart - you should be up and running.

If that doesn't work - check the build log of the Nvidia driver. You will find it at:\
/var/lib/dkms/nvidia-current/
Any error messages would give you some directions and what needs to be tweaked.

There is a good review in the following link that may help you:
[http://forums.opensuse.org/english/information-new-users/unreviewed-how-faq/430150-opensuse-graphic-card-practical-theory-guide-users.html](http://forums.opensuse.org/english/information-new-users/unreviewed-how-faq/430150-opensuse-graphic-card-practical-theory-guide-users.html)

Just scroll to the part on Nvidia drivers.

If you were following the high-tech news, just recently there was a public exchange of hmmm... adjectives... between Linus Torvalds (creator of Linux) and Nvidia corporations. Mr. Torvalds was really upset (to say the least) about Nvidia's poor support and willingness regarding their Linux drivers.

Hopefully some of the info and links here would do the trick for you.
Good luck!

---

### Post by Jon Hanna on 2012-07-17
> **tenmoi said:**
> Google 'how to install bumblebee on ubuntu 12.04' and install it and keep your fingers crossed.
Right now the instructions at [https://launchpad.net/~bumblebee/+archive/stable/]("https://launchpad.net/%7Ebumblebee/+archive/stable/") are working like a charm on my GT555M, while mere months ago it was a lot more hit-and-miss. I know it's not the same card, but they are similar so I'd hope that the move from hit-and-miss (and pin-the-tail-on-the-donkey configuration) to "it just works" applies there too.

[https://github.com/Bumblebee-Project/bumblebee-ui](https://github.com/Bumblebee-Project/bumblebee-ui) is good to have along-with, though I found two things flaky:

1. bumblebee-app-settings assumes something will have already created ~/.local/share/applications which may not be the case. Manually running 


mkdir ~/.local/share/applications


sorts that fine though


2. bumblebee-indicator seems to not work for a while after first install, but eventually does. I haven't been able to trace what the triggering condition is. It also needs to be manually added to start-up applications after it's decided to fix itself (the icon will be the bumblebee icon rather than the default script icon when it's going to work).


Bumblebee itself though is fantastic these days compared to the start of this year.

---

### Post by KaisaUbun2 on 2012-07-20
> **nick78 said:**
> Hi, 
I need your help, I just installed Ubuntu 12.04 on my XPS 17 and seems it does not recognize the graphic card.  I use an application called sysinfo to check my system information and when I click on the graphic card I can see this screen:



System details:

XPS L702X - i7-2670QM
XPS 72x BTS: 2nd generation Intel Core i7 - 267QM proc 2.20 GHz with Turbo
Display: 17.3in HD + WLED True-Life (1600 x 900) with 2.0 Mega Pixel Integrated
Memory: 6GB (1 x 4GB + 1 x 2GB 1333MHz DDR3 Dual Channel
Graphics: 1GB NVIDIA GeForce GT 550M Graphics Card



Does anybody have the same problem? 

Thanks
Nico

Yes, I had the exact same problem, Install this: 

```
sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo apt-get install bumblebee bumblebee-nvidia
```
then 

```
sudo apt-get install --reinstall nvidia-current
```
this should solve your problems. A heads up thought the HDMI port that comes with the graphic card is currently still unfunctional there are some solutions out there but its pretty dificult and costy

---

### Post by Jedcurtis on 2012-08-07
Hello all,
I also have an XPS 15z with an nvidia GeForce GT 540M graphics card. The system also has an Intel 2nd Gen Integrated Graphics Controller.  I hate to admit it, but it's looking optimus, I mean ominous!

When looking at the Details in System Settings, Graphics are Unknown. When I click on Graphics in the Details section of System Settings, it says Graphics Driver Unknown, and Experience Standard.

Does this mean that I'm not able to experience the 3D part of Unity?

I have installed Bumblebee, and am aware of how to start apps using the optirun cmd. I'm not much of a gamer, but I do like my eye-candy!  Battery life is of no import to me as my laptop is almost always on and plugged in.  I sit in my lazy-boy alot!!!  That said, I'd like to know that I'm using this machine to the fullest.

Like I said, I've got bumblebee installed, and am having no problems just want to be sure I'm having the best Ubuntu experience I possibly can!  I've been reading posts for days now, and there doesn't seem to be any consensus on the subject. (Well, except for not buying a laptop with Optimus technology, which unfortunately I already have!)

Any help/advice appreciated!

Jed

---

### Post by Scott Harrison on 2012-08-07
Or just download them from Nvidia directly?

[http://www.nvidia.com/object/linux-display-amd64-295.59-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.59-driver.html)

---

### Post by Jedcurtis on 2012-08-07
Like I mentioned in my previous post, I have the GT 540M nvidia card in my laptop.  I also have the integrated Intel video.

So what about all the posts warning me to NEVER install the nvidia driver by itself? Is this an updated driver that wont cause problems?

Thanks Jed
PS, I know I wasn't the originator of this thread, so pardon the interruption.

---

### Post by piperbarb on 2012-08-08
As others have recommended, install Bumblebee.   It works very well and is stable on my XPS 17 (L702x).  I have had no problems with it.  Just follow the instructions posted earlier in this thread.

---

### Post by Jedcurtis on 2012-08-08
I installed Bumblebee as one of the first things after getting 12.04 Precise Pangolin up and running.
I guess I'm just curious why the System Settings say Unknown when it comes to graphics.
I'd also like to know if I'm currently able to utilize the 3D settings.  I'd think that as long as Optimus has been around, nVidia would have been a little more supportive of the Linux community!  I've done a lot of reading here on UbuntuForums, and also at AskUbuntu.  It seems that there are enough frustrated users that something besides Bumblebee or Ironhide (I use bumblebee and have since the ominous Optimus situation).
Anyway, it is more of a nit-picky thing with me as my system does everything I want it to.
I'd just like for my hardware to actually be showing up correctly when I query it, or try to see real-time info...
Jed

---

### Post by Greggyboy on 2012-08-12
I haven't had any luck with bumblebee on my L702X, sure it works but the Nvidia GT555M is slower than the Intel!!!

Running the timedemo on ioquake @ 1440 x 900:

```
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce GT 555M/PCIe/SSE2
GL_VERSION: 4.2.0 NVIDIA 295.40

1260 frames 12.6 seconds **99.8 fps** 8.0/10.0/24.0/2.1 ms


```

And then on the Intel with vsync disabled (dri2)

```
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
GL_VERSION: 3.0 Mesa 8.0.2

1260 frames 6.2 seconds **201.8 fps** 3.0/5.0/11.0/1.2 ms

```

Not worth bothering with imo.

> **piperbarb said:**
> It works very well and is stable on my XPS 17 (L702x).  I have had no problems with it.

Is the nvidia slow like mine?

---

