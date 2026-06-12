---
title: "Random Compiz Crash"
date: 2009-04-28
forum: Desktop Environments
---

### Post by Baneblade on 2009-04-28
Im getting seemingly random crashes of Compiz frequently since installing 9.04 64bit. Any help as to the cause would be most appreciated.

Quick system specs just in case:

CPU: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
RAM: CORSAIR XMS3 DHX 4GB ( 2 X 2GB ) PC3-10666 1333MHz 240-pin DDR3 CL9
GPU: NVIDIA GeForce GTX 280
Mobo: XFX nForce 790i Ultra 3-Way SLI


Just had a complete freeze up too now. Nothing would move/click, though music was still playing fine. 
Restarted X, lost my work, but prevented a hard reboot :)

---

### Post by kvanderslice on 2009-04-28
I am getting this too - every hour or so I'll have to do a hard reboot of my machine (Alt + Sys RQ + REISUB)

Running an HP Compaq 8710w laptop, specs:

Intel Core 2 Duo T9500 @ 2.60GHz
2 GB Ram
Nvidia Quadro FX 1600M
HDA Intel Audio

I'm running the latest Nvidia 180.53?  Drivers, installed from the repos, as well as installed with EnvyNG.

I've also tried with the 170 drivers, and I don't crash, but my machine does do a hard lock up once every 20 minutes or so for about 6-7 seconds.

From what it looks like, it's a Compiz thing, since I can still move my mouse around and sometimes see the main menu drop down windows, but the screen usually turns black and flickers or just freezes.

---

### Post by pokogr on 2009-04-28
It might seem irrelevant but do you have virtualbox installed?

---

### Post by kvanderslice on 2009-04-28
Not at the moment, no.

---

### Post by kvanderslice on 2009-04-28
An update on this - I had the Compiz PPA repos enabled in Synaptic and had installed a plugin package from it.  I disabled the repos, reloaded the information, and reinstalled the packages and have yet to see my problem reoccur.

---

### Post by Baneblade on 2009-04-28
> **pokogr said:**
> It might seem irrelevant but do you have virtualbox installed?
No, i don't have it installed. Has this been known to cause a Compiz crash by just being installed?

---

### Post by chanders on 2009-04-29
Same random crashes here. Sometimes the mouse moves and I can see the desktop updating but cannot click. BTW I have vmware installed

---

### Post by kvanderslice on 2009-05-12
> **kvanderslice said:**
> An update on this - I had the Compiz PPA repos enabled in Synaptic and had installed a plugin package from it.  I disabled the repos, reloaded the information, and reinstalled the packages and have yet to see my problem reoccur.

Even with the PPA repos disabled I still have crashes.  Probably once every hour - 4 hours or so.  Can only restart with REISUB.

---

### Post by djodjoman on 2009-06-01
I'm also getting it! It seems related to some window event ... sometimes when a new windows or tab opens, it crashes ...

It worked fine for me on 8.10 ...

---

### Post by nightfrost on 2009-06-08
Seeing it here as well.
Has anyone filed a bug regarding this?

---

### Post by Baneblade on 2009-06-08
> **nightfrost said:**
> Seeing it here as well.
Has anyone filed a bug regarding this?

Until this is reproducible we cannot file a bug report and expect reliable support. I have yet to discover the cause of this yet, though i do believe it to be compiz related. Common theme here seems to be Nvidia cards + Compiz.
Who knows, perhaps when the drivers are updated this will all go away... here's hoping :)

---

### Post by TvL on 2009-07-13
Hi,

I'm using Ubuntu 9.04 64BIT.
Nvidia driver 180.44 on a Nvidia Quadro NVS 140M graphics card.
The laptop is a (IBM Thinkpad) Lenovo R61.

I am experiencing the same thing as you guys do.
When having compiz enabled my laptop freezes randomly. It will sometimes automatically reboot. 

It seems to happen randomly but I have a feeling that it happens more often while resizing a window. It used to crash my laptop about 2 to 5 times a day, but I have disabled compiz now and my problems have gone away (for now).

---

### Post by Baneblade on 2009-07-13
> **TvL said:**
> Hi,

I'm using Ubuntu 9.04 64BIT.
Nvidia driver 180.44 on a Nvidia Quadro NVS 140M graphics card.
The laptop is a (IBM Thinkpad) Lenovo R61.

I am experiencing the same thing as you guys do.
When having compiz enabled my laptop freezes randomly. It will sometimes automatically reboot. 

It seems to happen randomly but I have a feeling that it happens more often while resizing a window. It used to crash my laptop about 2 to 5 times a day, but I have disabled compiz now and my problems have gone away (for now).

The fact that your machine is rebooting sometimes after freezing up makes me think that you may have a heat dissapation issue there. The fact that it only happens when compiz is enabled makes sense, as compiz gives the GPU extra workload.

Have you tried running a cooler under your laptop? Or even a desk fan blowing onto your machine would help. Try that and see if it stops the laptop rebooting.

---

### Post by Baneblade on 2009-07-13
An update: Haven't had freeze ups recently, and i cant remember the last time compiz crashed (fingers crossed here).
I have been keeping my machine up to date with the latest patches, and have made no hardware changes other than a new CPU cooler, so i can only assume this has been fixed by an update?
Anyone else still getting this problem?

---

### Post by ptesone on 2009-07-23
I'm getting random Ubuntu 9.04 lock ups, I don't know what's causing it. . .

I'm using a 750a SLI mb with AMD phenom quad core. . .

---

### Post by craftbrewer on 2009-09-12
Just another data point.  I've got an nForce 750a SLI/AMD dualcore mobo.  GPU temp hovers around 45'C.  The PC itself doesn't hang, I can ssh in and kill Xorg to restore, and the GPU core temp when I've checked is still around 45'C.  Every time it has happened has been either resizing a window or while a tooltip overlay is being drawn.  

This only started happening on a virgin install of Ubuntu 9.04 AMD64.  I had no issues on my UbuntuStudio 9.04 partition which was originally an 8.04/8.10 upgraded to 9.04.  Unfortunately it committed apt-get autoremove suicide and I've since deleted it, so I cannot go back to compare settings and configuration.

---

### Post by dmuir on 2010-02-16
I think I've got the same problem. Mouse input barely works (pointer moves around, but clicks aren't registering), but I still have some control with the keyboard, so I can open up a terminal window.

I've got a Compaq 8510w with nVidia card.
Will try with compiz disabled for a while to see if the problem persists.

When it crashed, I tried killing compiz from terminal, but it wasn't running. Metacity was running, so I killed that and restarted it, but even with metacity running, I couldn't move windows, or alt+tab etc. So my guess is that the issue is further down the chain. Maybe xorg or nvidia drivers?

I've gone for days without any problems, then today I've had to reboot twice... rather annoying.

---

### Post by dmuir on 2010-02-24
Was working great with Metacity, then today it decided to go bonkers too. Mouse clicks wouldn't register on anything other than the panel, but keyboard commands worked fine. The problem was still there on reboot. Was able to fix by swapping back to compiz.

---

### Post by dmuir on 2010-02-24
Hmm, I take that back. The issue is different, and was not fixed by swapping back to compiz.

Seems that mouse controls "stick" to a given window. To "unstick" you need to click on the menu for the app, then you can click on other apps. Otherwise, you're stuck within the app.

Better explanation:
If I'm in firefox, and I click anywhere on a page (lets call it the viewport), mouse clicks will now only register on the viewport. Even trying to move the window won't work. Once I've clicked on, for instance "File" in the menu, mouse clicks now register outside of the viewport.

Am about to try newer drivers from nvidia.

---

