---
title: "GTX 750 TI will able to play Borderlands 2"
date: 2015-01-02
forum: Gaming &amp; Leisure
---

### Post by bizhat on 2015-01-02
Anyone playing Borderlands 2 on GTX 750 TI ?

Can you please post some screenshots ?

I am consider upgrading my GPU. I want low power GPU, don't want to spend too much for GTX 970/980, may be i can afford GTX 960 when they release it, but again, initial price will be high. Should i wait for it or just get a GTX 750 TI ?

---

### Post by efflandt on 2015-01-03
I just got an MSI TwinFrozr Gaming GTX 750 Ti. It was a bit long with the twin fans, so I had to relocate my hard drive, but there are single fan versions that are quite short and probably all that is needed for this efficient Maxwell chip. When I run it to the max the twin fans barely speed up a couple of percent from it 32% base with no noticeable noise at all. The card only uses 60 watts max (vs. 116w for my GTX 550 Ti), so my whole computer only uses about 150 watts max vs. 200 and at idle uses 50 vs. 75 watts. I have not played Borderlands 2, but in Team Fortress 2 the fps is triple digits most of the time in High settings with 8XAA @ 1080p. For Unigine Valley benchmark it is about twice as fast as my GTX 550 Ti and more than twice as fast (on half the power) if the GTX 750 Ti is overclocked.

The most video demanding Steam game I have is The Talos Principle which has very detailed and realistic looking graphics. For my GTX 550 Ti the default was for it to render the graphics at 1600x900 and upconvert that to 1080p. But with this GTX 750 Ti I can have it directly rendered at 1920x1080 which really looks good and is still quick enough.

The only snag I ran into was doing a fresh install of 64-bit 14.04. The card worked fine in my 64-bit 12.04 system using an nvidia 331 version (I think the result of nvidia-experimental-310 long ago). Not sure what the 14.04 live/install iso uses for graphics. That worked, but the in the installed system, not sure if nouveau supports Maxwell chips yet and the ancient 304 version of nvidia-current did not support this chip, so I had no gui. The nvidia-331 can work, but I added the xorg-edgers ppa and installed nvidia-346 and related nvidia-settings. With this driver it is possible to set cool-bits to 8 to be able to overclock gpu & RAM or 12 to also control the fan, from Nvidia X Server Settings.

---

### Post by bizhat on 2015-01-03
Thank you @efflandt for the reply. This is the exact model i am considering to buy or ASUS one with 2 Fans. Thanks for all the info. As for driver, can't you just install driver from nvidia web site ? Not sure how this is done, for AMD, you can download catalyst from AMD site if you want to use non open source driver.

---

### Post by oldrocker99 on 2015-01-03
I was able to play Borderlands 2 on Windows with a 650ti, so I have little doubt that a 750ti (which is faster:[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)) can give excellent results, unless you're a framerate junkie;).

---

### Post by Drone4four on 2015-01-04
**@efflandt**: That was a very well written and helpful piece of prose. Thanks for sharing. I'm not in the market for a GPU right now, but your informative post has helped **bizhat** and who ever else has stumbled upon this thread.

---

### Post by efflandt on 2015-01-05
Installing a driver directly from nvidia website for Linux in the past (which might require manually installing dkms package and making sure that you have kernel headers) has been somewhat troublesome because that was not recognized by the system updates, so whenever you got a new kernel, you had to rerun the nvidia installer script for the drivers. And sometimes there could be inconsistencies with the X server. Not sure if that has changed in newer Ubuntu versions to automaticall update video modules for drivers installed outside of the usual package system.

By using the repositories, either a newer driver in standard repos or adding the xorg-edgers ppa to the repos, when you get a new kernel, the nvidia modules for it are upgraded for that kernel version automatically. The only potential snag with using ppa is that you need to use ppa-purge to remove the ppa from the repo list and remove those drivers (installing standard Ubuntu video drivers that work) before upgrading an existing system to newer Ubuntu version. But I normally do a fresh install for a newer version after backing up anything I want to save (I recursively copied (cp -r) my home directory to ext4 partition on external USB drive, then copied that to the new system when replacing 12.04 with fresh 14.04). Many people have a separate /home partition that they can mount after installing a new system.

---

### Post by oldrocker99 on 2015-01-06
Finally got my desktop running, with my 750ti, and Linux Borderlands 2 rns very well.

---

