---
title: "Launchbar with Fluxbox?"
date: 2012-07-13
forum: Desktop Environments
---

### Post by Thunder7102 on 2012-07-13
Hello everyone. I recently installed Ubuntu and I came from attempting to get a working setup of Archlinux. Unfortunately, I did not and do not have the free time to sit down and configure everything until I have a working system. I needed something that came out of the box and 'worked' and I could customize later. Ubuntu seemed like a great choice. 


Anyhow, I am currently running Ubuntu 12.04 on Gnome 3(I believe that is it), and am wanting to move to a more fluxbox-like environment with a launchbar at the bottom which hides itself until I move the mouse down there (I would prefer it do this on top of windows as well). Are there any application docks that are decently customizable that operate well with fluxbox? Compatibility with workstations would also be appreciated (gnome's customizable workstation setup). 

I really dislike going through gnome's top hotbar to find things I just want to launch "now" and i can't find anything on the Unity bar as it does not show everything and i never took the time to learn how to find all my programs from it. 

A little system information:
Running latest updates, Ubuntu 12.04
RAM: 6GB
Processor: AMD Athlon II 4x 2.8GHz
Nvidia GTS 450 1.3GB OC'd Running dual-display

---

### Post by Version Dependency on 2012-07-13
You could try the tint2 panel. It can be set to intellihide.  Or install any of the popular docks such as cairo-dock or docky.

---

### Post by Thunder7102 on 2012-07-13
> **Version Dependency said:**
> You could try the tint2 panel. It can be set to intellihide.  Or install any of the popular docks such as cairo-dock or docky.

I heard they all have a compiz dependency. Cairo-dock gives me a black box because for some reason, compiz simply does not wish to run on my computer. I had this exact problem in archlinux. I was completely unable to run anything based on compiz for whatever reason. 


And will tint2 support multiple workspaces? It sounds like a good alternative to try.

---

### Post by Version Dependency on 2012-07-13
> **Thunder7102 said:**
> I heard they all have a compiz dependency. Cairo-dock gives me a black box because for some reason, compiz simply does not wish to run on my computer. I had this exact problem in archlinux. I was completely unable to run anything based on compiz for whatever reason. 


And will tint2 support multiple workspaces? It sounds like a good alternative to try.

The black box around cairo-dock is because you need compositing.  Some window managers have compositing built-in, like Compiz and Kwin.  The lightweight window managers like openbox, fluxbox, pekwm, etc. will require you to install a composite manager to enable compositing.  You can install xcompmgr for this.  Set it to run at startup in fluxbox and your dock should now have a transparent background instead of that black box.  As for the dependencies, I wouldn't worry about that.  It installs some libraries to make certain applets work correctly.  And if you are adding this fluxbox session to the standard Ubuntu 12.04, then you probably have most of the Gnome/Compiz dependencies Cairo Dock needs anyway.

Tint2 is a great panel and has some support for multiple desktops. It doesn't come with any kind of workspace switcher, but instead allows you to separate the taskbar in a way that programs in workspace 1 open on one section of the taskbar, programs open in workspace 2 open in the next section of the taskbar, etc.

---

### Post by Rodney9 on 2012-07-13
Good tint2 tutorial - 

[https://code.google.com/p/tint2/wiki/Configure](https://code.google.com/p/tint2/wiki/Configure)

[http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/](http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/)


Fluxbox Guide

[http://tinyurl.com/7yf5o6s](http://tinyurl.com/7yf5o6s)

Openbox Guide

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Rodney

---

### Post by andrew.46 on 2012-07-28
> **Thunder7102 said:**
> Unfortunately, I did not and do not have the free time to sit down and configure everything until I have a working system. I needed something that came out of the box and 'worked' and I could customize later. Ubuntu seemed like a great choice. 

But perhaps Fluxbox is not such a good choice then? I have used Fluxbox for some time and while it is a beautiful window manager some considerable time and effort is involved to get a full working setup. Well worth the time, IMHO, but if you don't have the time....

---

