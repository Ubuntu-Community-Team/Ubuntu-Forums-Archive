---
title: "Advanced Desktop Effects and nVidia  GeForce 8400M GS"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by budajeff on 2008-04-12
I'm running ubuntu 8.04 on a Dell Inspiron 1520 laptop with a nVidia Corporation GeForce 8400M GS (rev a1) graphics card.

Whenever I reboot after enabling the nVidia driver for my GeForce 8400M GS (rev a1) graphics card, my display is unreadable and I have to reboot again and use the recovery boot to reinitialize my x server.

So far I've tried to enable Advanced Desktop Effects in two ways: via the System->Preferences->Appearance menu item, and via EnvyNG. In either case, after the reboot, the display is unusable in exactly the same way. 

Any ideas on how to troubleshoot this?

Has anyone gotten 8.04 w/ Advanced Desktop Effects working w/ a nVidia GeForce 8400M GS?

Would I have better luck if I tried a previous version of Ubuntu?

Thanks,
Jeff

---

### Post by budajeff on 2008-04-15
**This post could be related to an Ubuntu bug filed at**:  [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm all set.

I had to download and install the beta driver for my graphics card.

It took a weekend, but I finally found this bug report the clued me in:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718)

jb

---

### Post by zhinker on 2008-04-24
I'm having the same problem.  How do you install the beta drivers?  (I'm not too experienced with that stuff)

Thanks

---

### Post by Jrichalot on 2008-04-27
Budajeff, can you post your xorg.conf ?
I have just updated to Heron and lost proper resolution. Using the restricted driver in Heron did not make a difference. I am also on an Inspiron 1520 with an nVidia GeForce 8400M GS (rev a1). Resolution and effects were perfect under Gibbon.
Cheers
Jerome

---

### Post by n00biwan_ken00bi on 2008-05-29
Hi Guys,

Maybe this helps:

[http://www.nvidia.co.uk/object/linux_display_amd64_173.14.05_uk.html](http://www.nvidia.co.uk/object/linux_display_amd64_173.14.05_uk.html)
----------------------------------------
Linux x64 (AMD64/EM64T) Display Driver

 
Version: 173.14.05
Operating System: Linux x64 (AMD64/EM64T)
Release Date: 28.05.2008 

Release Highlights 

Added support for the following new GPUs: 
Quadro FX 3600M 
GeForce 9800 GX2 
GeForce 9800 GTX 
GeForce 9600 GT 
GeForce 9600 GSO 
GeForce 9600 GS 
GeForce 9500M GS 
GeForce 8400 
GeForce 8400 GS 
Added support for Quadro FX 5600/4600 SDI and Quadro G-Sync II. 
Resolved a bug causing left and right eyes to be reversed in stereo mode on some Quadro FX GPUs. 
Fixed a problem that caused OpenGL to stop rendering to windows with origins at or beyond 4096 pixels (horizontally) on GeForce 8 and 9 GPUs. 
Fixed a bug causing some Quadro FX 4500 SDI configurations to take a long time to achieve synchronization. 
Added preliminary support for X.Org server 1.5. 
Addressed a problem causing visual corruption when using GeForce 8 GPUs to drive Chi Mei 56" displays. 
Addressed visual corruption when driving Cintiq 20WSX wide format tables with some GeForce 6 and 7 GPUs. 
Fixed OpenGL rendering corruption with textures compressed using the DXT5 compression algorithm. 
Fixed a regression that caused invalid EDIDs to be detected for the internal display device on some notebooks. 
Improved hotkey switching and power management support on some GeForce 8 notebooks. 
Fixed a regression causing some GeForce 6100/6150 systems to fail to restore the screen after DPMS cycles. 
Fixed a bug that prevented the console from being restored correctly in SLI mode on GeForce 6 and 7 GPUs. 
Fixed interlaced modes on GeForce 8 GPUs. 
Fixed a problem that caused the synchronization signal polarity to always be positive for DVI devices on GeForce 8 and 9 GPUs. 
Resolved a problem resulting in X startup to fail on some GeForce 8 and 9 systems without swap space. 
Fixed a bug resulting in X crashes when using GeForce 8 and 9 GPUs in SLI to drive X screens at depth 8. 
Fixed a problem that caused TV output on secondary TVs to be black and white on some GPUs. 
Restored compatibility with recent Linux 2.6 kernels. 
---------------------------------------------- 

Its for 64 bit processors should be one somewhere there for 32 bit ones as well...

---

