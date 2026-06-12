---
title: "computer slows to crawl after recent system update"
date: 2011-06-17
forum: Desktop Environments
---

### Post by 13east on 2011-06-17
(thinkpad edge14 w/ i3-370M(2.4GHz), 4GB RAM, Intel HD Graphics & Kubuntu 11.04 x64)

Extreme slow down in performance/extreme choppy graphics performance starting only recently after a system update that brought along w/ it Firefox5beta.

Switching over to xrender seems to have solved the issues. I much prefer to stay under xrender because the system seems to run/looks much smoother than under OpenGL:

1. Are there any benefits to running under OpenGL over Xrender?

2. Only feature that I miss is the blur effect under the taskbar; is there any way to emulate the blur effect under xrender w/ qtcurve and oxygen desktop theme?

3. The only performance related issue that I've noticed under Xrender was when running Diablo II:LOD under wine. Are there any tweaks/patches/configuration to ensure smooth graphics performance (game play and video playback) w/ xrender?

Any help that anyone can provide would be very much appreciated.
Thank You.

---

### Post by ankspo71 on 2011-06-18
Hi,
Some of this is only general advice for gaming and general advice for KDE desktop performance, but some of it might help... and some of it also might help with the desktop crashing as described in your other thread [http://ubuntuforums.org/showthread.php?t=1784763](http://ubuntuforums.org/showthread.php?t=1784763)

First open your terminal (konsole) and use the command 'top' to see if you can find what is causing any performance problems. There could be an application that is using too much CPU power or using too much memory. Any application doing that can drastically effect desktop performance. In some cases, certain applications can be safely killed (or disabled from autostarting) and the desktop performance would return to normal. If not, at least you might now have an idea on what could be causing the poor performance.

> 1. Are there any benefits to running under OpenGL over Xrender?
From what I understand, and I could be wrong, but I think the noticeable difference between OpenGL and Xrender, is OpenGL is much better for handling graphics and effects because it has more function calls to do so. Xrender feels much lighter because it has less function calls that can be done. 

OpenGL has over 250 different function calls to draw graphics, according to this link:
[http://en.wikipedia.org/wiki/Opengl](http://en.wikipedia.org/wiki/Opengl)
Xrender basically only supports 2D graphics (and maybe some 3D?), translucency, anti-aliasing and shadows, according to these links:
[http://en.wikipedia.org/wiki/Xrender](http://en.wikipedia.org/wiki/Xrender)
[http://wiki.x.org/wiki/Development/Documentation/Glossary?action=show&redirect=XorgGlossary](http://wiki.x.org/wiki/Development/Documentation/Glossary?action=show&redirect=XorgGlossary)

> 2. Only feature that I miss is the blur effect under the taskbar; is there any way to emulate the blur effect under xrender w/ qtcurve and oxygen desktop theme?

This is going to be inconvenient and is only a fake way to do it, but the only thing I can think of is to edit the wallpaper in Gimp to add some Gaussian Blur the bottom portion of your wallpaper. If you only use one wallpaper, then this might be worth doing.

> 3. The only performance related issue that I've noticed under Xrender was when running Diablo II:LOD under wine. Are there any tweaks/patches/configuration to ensure smooth graphics performance (game play and video playback) w/ xrender?

There are several things that can be done to improve gaming performance, including changing some of the options inside the game itself, and things like changing your screen resolution to derease the load on your graphics card, changing your monitor's refresh rate (if possible), turn off or reduce anti-aliasing etc, but as for changing KDE specific settings...

Go to System Settings > Application Appearance > Style > Fine Tuning.
For "Graphical Effects", choose "Low display resolution and low CPU"
That will turn down the quality of the graphics used to display your desktop. The change in visual quality isn't very noticeable though.

Now go to System Settings > Desktop Effects > General.
Change Animation Speed to Fast. (this will only help performance of the desktop, but it helps alot)
You can also experiment with the "keep window thumbnails" and "scale method" options.
Same with "OpenGL Mode" if you switch back to OpenGL.

Now go to System Settings > Desktop Effects > Advanced.
Disable: Use functionality checks. <-- functionality checks can cause crashes for some people.
Enable: Suspend desktop effects for fullscreen windows.
Disable: Use Vsync 

See this article about Vsync and game framerates:
[http://hardforum.com/showthread.php?t=928593](http://hardforum.com/showthread.php?t=928593)

You might need to log out and log back in for some changes to take effect, depending on the options being changed.

--- Other ---

There are two other things I like to do to improve gaming performance but they have nothing to do with the KDE desktop, and that is to install an ultra-lightweight window manager along side my KDE desktop (and by doing so it eliminates all performance problems caused by KDE's running processes), and I use some file system tweaks to improve filesystem performance.

I like using openbox for a light weight window manager because I like using obmenu to edit my menus.

The tweaks I use on the filesystem are here:
[http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/)

---

### Post by wildmanne39 on 2011-06-18
> **13east said:**
> (thinkpad edge14 w/ i3-370M(2.4GHz), 4GB RAM, Intel HD Graphics & Kubuntu 11.04 x64)

Extreme slow down in performance/extreme choppy graphics performance starting only recently after a system update that brought along w/ it Firefox5beta.

Switching over to xrender seems to have solved the issues. I much prefer to stay under xrender because the system seems to run/looks much smoother than under OpenGL:

1. Are there any benefits to running under OpenGL over Xrender?

2. Only feature that I miss is the blur effect under the taskbar; is there any way to emulate the blur effect under xrender w/ qtcurve and oxygen desktop theme?

3. The only performance related issue that I've noticed under Xrender was when running Diablo II:LOD under wine. Are there any tweaks/patches/configuration to ensure smooth graphics performance (game play and video playback) w/ xrender?

Any help that anyone can provide would be very much appreciated.
Thank You.
Hi, I to got updates that effect performance, I went into update manager and changed updates so I would not get prerelease updates anymore. Firefox 5.0 beta casused some problems also, I do not know an easy way to get rid of the installed update that are causing the problem though. I do have a link for people have problems with choppy and slowness.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by 13east on 2011-06-19
> **wildmanne39 said:**
> Hi, I to got updates that effect performance, I went into update manager and changed updates so I would not get prerelease updates anymore. Firefox 5.0 beta casused some problems also, I do not know an easy way to get rid of the installed update that are causing the problem though. I do have a link for people have problems with choppy and slowness.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

The link you posted is not valid for Kubuntu, as CompizConfigSettingsManager has no effect on kde desktop only gnome (at least in my case).

---

### Post by wildmanne39 on 2011-06-19
> **13east said:**
> The link you posted is not valid for Kubuntu, as CompizConfigSettingsManager has no effect on kde desktop only gnome (at least in my case).Hi, I was hoping that would give you a general idea of what to look for, it is included in kubuntu also sync to vblank and, I remember several weeks ago helping someone change that setting in kubuntu and it fixed is problem and think that other one is direct rendering but I do not remember for sure, they are both in kubuntu, you will have to look for them I do not have kubuntu installed anymore.

---

