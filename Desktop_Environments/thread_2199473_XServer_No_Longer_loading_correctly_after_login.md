---
title: "XServer No Longer loading correctly after login"
date: 2014-01-14
forum: Desktop Environments
---

### Post by PipIWYG on 2014-01-14
Hi Guys,

I seem to be at a dead end regarding my desktop and display drivers. Long story short, I bought a VGA to HDMI converter for an old external HP Monitor (HP LE1901w). I hooked it up through my HDMI port and it was working fine for a few days. But then I closed the lid of my laptop, and the machine went into hibernation. Since then, the external wouldn't go on at all, nor would it be detected in the Display Properties in Ubuntu Settings.

I then proceeded to scratch around online, and got the sharp idea of installing the proper NVIDIA drivers for my NVIDIA GeForce GT 740M. I did a whole pile of things, like apt-get nvidia-current, jockey-text updates, and more without any luck. I was still at a point where I could revert these changes, and boot back into X without problems, but then I found a site that had a link to a .run driver package installer on the nvidia web site. After this install I was no longer able to revert back to previous configuration. I even uninstalled it, and still, no fix.

So basically, my problem is as follows... I've disconnected the HDMI display, and all I'm really trying to do is to get my desktop to work properly again just on my laptop display. When I boot into X, the logon screen comes up fine. When I logon it just goes into a blank black screen with a mouse pointer. I can press Ctrl+Alt+T to get a terminal window, without a titlebar or anything to resize or move the window around. From there I can launch apps like chromium-browser, one at a time. If I run nautilus, my desktop wallpaper comes back with all the icons on my desktop, but no taskbar, or unity menu or ciaro dock loads. So that's where I am now, and I am out of options.

I would really just like to get the desktop environment back to where it was. The external monitor issue I can do some more research on at a later stage, but right now I need it up and running.

A few details on my specs:
Laptop: HP ENVY 17 Notebook
CPU: Intel i7-4700MQ (2.4GHz)
GPU: NVIDIA GeForce GT740M (2GB)
OS: Ubuntu 13.10 (Saucy) 3.11.0-15-generic

I was really hoping someone could possibly point me into the right direction.

Thank you.

---

### Post by steeldriver on 2014-01-14
It sounds more like a desktop session issue than an actual graphics card / driver issue - can you log in as guest? or create a new user and log in with that account? 

If guest account looks OK the first thing I would try is resetting compiz in your main account

```

sudo apt-get install dconf-tools

dconf reset -f /org/compiz/

setsid unity

```

see [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by PipIWYG on 2014-01-14
Hi steeldriver,

I have a VNC account which I've used, and when selecting "Ubuntu" as my desktop option the same thing happens. However, I do also have an XFCE Desktop Environment, and when I selected that it worked fine, but then I tried to start unity and compiz which made that session do the same thing. So then I downloaded kubuntu-desktop, which works fine, but the original ubuntu session no longer works for any user.

I did do a dconf reset -f /org/compiz and setsid unity, but it did not work. If I had to reinstall ubuntu-desktop, would that reset everything? Thing is, selecting ubuntu session even with kubuntu also doesn't work.

---

### Post by steeldriver on 2014-01-14
In my experience, the Unity-based ubuntu-desktop works poorly via VNC so that's not really a good test - it would be better to try the guest account, or to create a new user account and try that. That will help to narrow the problem down to whether it is just something in the personal config/cache files of your user session or something related to the ubuntu-desktop itself.

---

