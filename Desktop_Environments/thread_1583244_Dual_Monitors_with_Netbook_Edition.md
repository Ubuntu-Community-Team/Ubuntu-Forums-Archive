---
title: "Dual Monitors with Netbook Edition?"
date: 2010-09-27
forum: Desktop Environments
---

### Post by quutar on 2010-09-27
I have an [Acer Aspire Revo 3610]("http://support.acer.com/acerpanam/desktop/2009/acer/aspire/AspireR3610/AspireR3610sp2.shtml") that I am installing Ubuntu on. I personally like the Netbook (and I really like the Unity interface more) interface and decided to install that one on my machine. The problem comes in when I try to enable two monitors.

I have tested this with the 10.04 and the "beta" 10.10 builds, it is pretty much identical.

first, I install Ubuntu fresh from CD. Both monitors are "working" but mirrored of each other. (I have a USB DVD-R for installations)
I then use the driver program and install the proprietary NVidia drivers, at this point the second monitor turns off.
Finally I use the package manager and update the system

At this point I go down two paths, both of which fail

If i want to try staying with 10.04 I go into the nvidia display application and enable the second monitor. It requires a reboot (of at least X, i can log out and then back in if needed, but I tend to reboot the entire computer just in case... results are the same).

After the reboot the desktop never shows up. After asking me for my username/pass the screen acts like it is about to load the UI and then flickers, and 5 seconds layer flickers, again... and 5 seconds later... etc. This keeps happening until I shut the computer down, or use ALT-control-delete to try to log out (flickering makes it hard)

When I enabled the second monitor, it was as an independent display, not a shared "single monitor" style (I think it was called twinview? I am not at that computer right now)

I also tried this down a second path, seeing if this was fixed in 10.10

So, I re install ubuntu desktop, going down the same path as above... except before I enable the second monitor, I to "package-manager -d" and upgrade to 10.10 netbook edition. I also tried downloading the maverick desktop cd and installing straight from there, but the results are the same.

Unity is now nice and shiney and my desktop UI. I go into the nvidia display manager, enable the second monitor, just like 10.04, and I go into the same display loop... nothing happens.

Is the netbook UI just not made for dual monitors? do I need to use the option that merges both monitors into one?

------------------------------------------
the reason I want to be able to do this is kind of weird... I am trying to build a video playback "appliance", and this is just my playing with some, hopefully, out of the box options.

What I want is a linux computer with two monitors (revo is my current hardware target)
I want one monitor to be the GUI, restricting the mouse and everything user interface wise to that screen. (I have not figured out how to do this yet, even in windows)
I want the second monitor to be unadorned, which mplayer will use as a display target. (I can do this under windows)

I have tried the dual monitor solution with Ubuntu Desktop... but the second monitor was not unadorned, and I had allot of video tearing due to the windows manager... I really like the UI for the desktop edition, and was hoping i could get it to do what I want.

---

### Post by darkstarbyte on 2010-09-28
For me I just hooked up another monitor through the vga port, but then again all my drivers are open source. 

One problem I have found on many popular operating systems is they like to make both screens perform to the lowest resolution of the two and shrink desktop of the highest resolution monitor to the lowest so it does not take up the whole screen.

On Linux I have found it tries to use the highest resolution cutting stuff of the low resolution screen.

---

### Post by quutar on 2010-09-28
my problem is that I need VDPAU support, which means the restricted drivers

---

