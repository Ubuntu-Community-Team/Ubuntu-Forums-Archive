---
title: "Low quality desktop experience with Ubuntu 13.10"
date: 2013-12-18
forum: Desktop Environments
---

### Post by G1imt on 2013-12-18
I recently jumped back into the Ubuntu world after about a year with Windows. This time I felt bold and installed the newest version, 13.10.

I have installed the newest Nvidia drivers, both the 64-bit and 32-bit ones, and tested that they work well by trying out several games on Steam.

My issue is that the, for lack of better words, "graphical desktop experience" (moving windows around, using window spread, expo etc.) is of very poor quality and performance. Moving windows around seems jumpy and looks to me like it's locked to 24/30 FPS. The same is true for window spread and expo, and additionally all down-scaling of textures is done without smoothing, so everything looks ugly and pixelated. Windows also have a tendency of going completely black during animations, and some times staying black for ever after the animation (usually fixed by minimizing and restoring the window again). Take a look at the screenshot I took midway through minimizing Chrome:



I can remember using Ubuntu 10 quite a while ago, and every animation and effect was smooth and beautiful. Shouldn't that also be the case now? Can you guys help me figure it out? Here is the little basic information I know how to provide you:

```

$ ldconfig -p | grep libGL
    libGLU.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGLU.so.1
    libGLU.so.1 (libc6) => /usr/lib/i386-linux-gnu/libGLU.so.1
    libGLEWmx.so.1.8 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGLEWmx.so.1.8
    libGLEW.so.1.8 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGLEW.so.1.8
    libGLESv2.so.2 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/mesa-egl/libGLESv2.so.2
    libGLESv2.so.2 (libc6) => /usr/lib32/libGLESv2.so.2
    libGLESv2.so (libc6) => /usr/lib32/libGLESv2.so
    libGLESv1_CM.so.1 (libc6) => /usr/lib32/libGLESv1_CM.so.1
    libGLESv1_CM.so (libc6) => /usr/lib32/libGLESv1_CM.so
    libGL.so.1 (libc6,x86-64) => /usr/lib/libGL.so.1
    libGL.so.1 (libc6) => /usr/lib32/libGL.so.1
    libGL.so (libc6,x86-64) => /usr/lib/libGL.so
    libGL.so (libc6) => /usr/lib32/libGL.so

```

My glxinfo output: [http://pastebin.com/raw.php?i=a2DnnBgA](http://pastebin.com/raw.php?i=a2DnnBgA)

I have an i7 3700K processor clocked to 4.3 GHZ, 16 GB 1600hz RAM and a 256GB SSD disk, Nvidia GTX 7800 and 3 monitors. The issue should not be hardware related.

---

### Post by ibjsb4 on 2013-12-19
> I can remember using Ubuntu 10 quite a while ago, and every animation and effect was smooth and beautiful. Shouldn't that also be the case now? Can you guys help me figure it out? 

 I can&#8217;t help you with the Unity desktop, but wish to let you know of an option ..

 You can install the Classic (fallback) desktop to your current install.  It is like the old desktop (you called it Ubuntu 10).  Maybe that will be more to your liking.  To install in terminal:
 
```
sudo apt-get install gnome-panel
``` 

At boot (login window) click on the icon and choose your desktop.

 [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by grahammechanical on 2013-12-19
What hardware do you have? CPU? RAM? Graphics card memory? I have found that certain PDF documents use a lot of RAM. You have Evince open. You are also running Transmission, a Bit torrent client. That will take up CPU, RAM and internet bandwidth. And all this at the same time as using a web browser. Do you also have Virtual Box open?  If so, that will put a massive hit on video capabilities.

So, in my opinion a lot depends upon the hardware in this machine and whether you are asking too much of it. You may need to enlarge the cache size of some of those programs. I have found that the system can have plenty of spare CPU power and RAM but some applications will grey out (such as Libreoffice). I put it down to have a too small cache for the application.

You can install System Load Indicator. That will give a real time readout of what is happening to CPU and RAM and other stuff. Ubuntu now sets aside some Free memory as cache/buffer memory to reduce the need to swap data to the swap partition. I have also noticed a 15 - 20% drop of memory usage (1GB) from 12.04 to 13.10. So, things are getting better. Ubuntu desktop is benefiting from improvements made in Ubuntu phones.

Regards.

---

### Post by VMC on 2013-12-19
[G1imt]("http://ubuntuforums.org/member.php?u=937946"), I have a similar experience using Ubuntu. Its best using *nouveau*, than *nvidia*, but *nouveau* freezes at unknown times. So I'm stuck using *nvidia* drivers.

Both Xubuntu, and Gnome work the best. Smooth and fast.

---

### Post by G1imt on 2013-12-19
> **grahammechanical said:**
> What hardware do you have? CPU? RAM? Graphics card memory? I have found that certain PDF documents use a lot of RAM. You have Evince open. You are also running Transmission, a Bit torrent client. That will take up CPU, RAM and internet bandwidth. And all this at the same time as using a web browser. Do you also have Virtual Box open? If so, that will put a massive hit on video capabilities.

So, in my opinion a lot depends upon the hardware in this machine and whether you are asking too much of it. You may need to enlarge the cache size of some of those programs. I have found that the system can have plenty of spare CPU power and RAM but some applications will grey out (such as Libreoffice). I put it down to have a too small cache for the application.

You can install System Load Indicator. That will give a real time readout of what is happening to CPU and RAM and other stuff. Ubuntu now sets aside some Free memory as cache/buffer memory to reduce the need to swap data to the swap partition. I have also noticed a 15 - 20% drop of memory usage (1GB) from 12.04 to 13.10. So, things are getting better. Ubuntu desktop is benefiting from improvements made in Ubuntu phones.

Regards.

That's not the issue. The desktop experience is identical whether I only have one window open or 20. I added my PC specs to the post, it shouldn't be a hardware issue.

---

### Post by ibjsb4 on 2013-12-20
Well your box has just about enough horse power to run the forum :)
 
Your running compiz as a window manager, which is a good choice for your box.  But I wonder if its causing the problem.  Again post#2; install fallback and switch your desktop at to &#8220;Classic (no effects)&#8221;.
 
Like I say, you should be running compiz, but this will allow you to test your box on metacity window manager (which no-effects uses) and eliminating compiz as a problem.

 Also, are you running Ubuntu in a virtual machine?

---

### Post by G1imt on 2013-12-21
Thanks ibjsb4. I will try your suggestions later today, after some Christmas shopping. I'm not using a VM, Ubuntu is installed directly on the second partition of my disk (Wintendo being on the first partition.)

---

### Post by oldrocker99 on 2013-12-21
I answered another question about the "old" Ubuntu here:

[http://ubuntuforums.org/showthread.php?t=2194645](http://ubuntuforums.org/showthread.php?t=2194645)

I hope that this is closer to what you're looking for.

---

### Post by G1imt on 2013-12-21
I don't want my Ubuntu to look like old Ubuntu, I just want it to run smoothly.

---

### Post by oldrocker99 on 2013-12-21
Well, MATE does run pretty smoothly.

---

### Post by G1imt on 2013-12-26
> **ibjsb4 said:**
> Well your box has just about enough horse power to run the forum :)
 
Your running compiz as a window manager, which is a good choice for your box.  But I wonder if its causing the problem.  Again post#2; install fallback and switch your desktop at to “Classic (no effects)”.
 
Like I say, you should be running compiz, but this will allow you to test your box on metacity window manager (which no-effects uses) and eliminating compiz as a problem.

 Also, are you running Ubuntu in a virtual machine?

I'm sorry, I never got to run your test. I installed Ubuntu 12.04 LTS and everything runs at a fast and smooth 60fps now. I'm using the exact same Nvidia driver version as I used on 13.10.

---

