---
title: "Gnome, Xinerama, Nvidia"
date: 2008-01-18
forum: Desktop Environments
---

### Post by cleric23 on 2008-01-18
Hi there,

today I tried to get my dual screen setup running. I am using a LCD and a CRT monitor, both connected to an Nvidia card. I am using Xinerama and in nvidia-settings, I choose "seperate X screen" instead of TwinView, since I dont want windows to get maximized over both screens and stuff, I read thats not possible with TwinView.

Okay, so. Everything works fine. But I dont want to use the second monitor all the time, I would rather like to switch it on and off on the fly (without restarting X). When I switch it off, I want all windows which where on it to be gathered on the first monitor (like it is in Windows or Mac OS X).

Is that possible? I read, that its possible with "xrandr", but unfortunately, xrandr segfaults (it doesnt if I use only one monitor). I noticed that RandR seems to get loaded twice (?) (once for every monitor), at least it looks like that in the Xorg.0.log.

My next question is about Gnome: How can I use different desktop background images for the different monitors? Right now, my one image gets scaled over both monitors, that really sucks.

I use 3 virtual desktops ("workspaces") in Gnome. Now, every workspace is as big as both monitors. Instead of having three double sized workspaces, I would rather like to have 3 workspaces per monitor (so when I switch workspaces on the first monitor, the second monitor stays where it is). Is that possible?

Thanks in advance!

Here are some specs, maybe they are important:
xrandr 1:1.0.2-0ubuntu1
Gnome 2.18.1
Kernel 2.6.20-16-generic x86_64
Nvidia driver: 100.14.11
x.org server vendor version: 7.2.0
Nvidia card: Geforce 8600 GT

---

### Post by OoooMatron on 2008-01-18
"choose "seperate X screen" instead of TwinView, since I dont want windows to get maximized over both screens and stuff, I read thats not possible with TwinView.
"

well that's incorrect for  a start. If you maximise the window on the left screen it fills the left screen only.

Isn't it easier just to test these things first rather than make comment on hearsay?

---

### Post by cleric23 on 2008-01-18
Okay, sorry, you are right. I just tried it. Now xrandr does not segfault anymore, but now, when I start glxgears or glxinfo or something else which wants to use 3D, X immediately crashes.

Any ideas? Anything for my other questions?

Thanks!

---

### Post by OoooMatron on 2008-01-19
I am not really sure about that stuff.

Concerning the wallpaper, I have just created a double sized wallpaper in the gimp with 2 pictures on it to display in either monitor since the background is treated as a single desktop and indeed stretches,

When i first tried this a couple of years ago I tried xinerama and used the option in that to create seperate desktops over the monitors. The only down side is that you cant drag windows between them but you can have completely seperate desktops that behave independently of each other.  Maybe you should try that. I cant remember how to activate it though.

The 3d gears works fine for me. All i have in my xorg is twinview enable line in the device and it's all cool.

---

