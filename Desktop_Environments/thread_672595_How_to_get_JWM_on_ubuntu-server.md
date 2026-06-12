---
title: "How to get JWM on ubuntu-server?"
date: 2008-01-19
forum: Desktop Environments
---

### Post by bone2006 on 2008-01-19
I was trying to get JWM on an old laptop running and I'm kind of stuck.  I installed ubuntu server with nothing selected, so that it's just the base system.  Then after installation I opened up the terminal and typed in
sudo apt-get install jwm and it told me it's going to only be 14mb, which kind of surprised me, but that's where I"m stuck.

I tried rebooting and I'm still at the terminal, so I tried typing in startx and it told me that I need to have xinit installed, but I wanted to post here before I start installing a bunch of things I really don't need.

---

### Post by bone2006 on 2008-01-19
found these instructions:
sudo apt-get install xorg jwm mc
then
startx

when it asked me about resolutions I didn't think I would need to remove, I left everything though..........hope I did it right.

Well after it starts it says

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

This is after it tries to start and returns to this..I tried startx again and samething.

Any help

---

### Post by kerry_s on 2008-01-19
yeah it's already screwed up if you tried to install jwm before X. you can remove both and try again with " sudo apt-get install xorg jwm mc " or just reinstall and use that line. it's a common problem most don't realize they need X before or at the same time as the wm or de. xorg does not auto detect wm's or de's, the environment puts the stuff for xorg, but if xorg is not there yet there's nowhere to put the settings. it has to go in the right order.

i recommend-> sudo apt-get install xorg jwm mc emelfm leafpad
jwm has to be setup from the start, emelfm is a very light filemanger, much like mc. leafpad is you text editor cause your going to have to edit the .jwmrc.

---

### Post by bone2006 on 2008-01-21
Kind of funny, I never tired leafpad, but I installed it one of my machines that has KDE to test the speed and compared it to mousepad.  I've been using mousepad for a long long time now and the speed has always impressed.  I tied to time and see which one can open faster and it was really hard for me to determine.

I can reinstall everything, because this system has nothing on it, so I don't mind reformatting my partition and starting all over again.

But your saying after the installation is complete with the server, I should be able to just do a "sudo apt-get install xorg jwm mc emelfm leafpad" and I'd be good to go?

Thanks for the help

A question, do you think JWM on ubuntu server is faster than xubuntu and flubuntu?  

I noticed that DSL and pupply Linux use JWM and was impressed with the speed, then saw that ubuntu server only requires 64MB of ram with just the basic.  So I thought that this might be a better solution for older systems.  Any thoughts?

---

### Post by kerry_s on 2008-01-26
> A question, do you think JWM on ubuntu server is faster than xubuntu and flubuntu?

I noticed that DSL and pupply Linux use JWM and was impressed with the speed, then saw that ubuntu server only requires 64MB of ram with just the basic. So I thought that this might be a better solution for older systems. Any thoughts?

I think JWM is faster, it's smaller to, but takes a while to get use to. i prefer it on debian myself, debian is faster and has less dependency's for the base install. jwm is still young as far as wm's go but i'm certain it is only getting better, it's only a matter of time that more distro's will use it and hopefully be a little easier for newcomers to set up. i use it as my main setup when using linux, i'm currently taking a linux break right now though.

> But your saying after the installation is complete with the server, I should be able to just do a "sudo apt-get install xorg jwm mc emelfm leafpad" and I'd be good to go?

yes just " startx " or you could add " gdm " to that command, then just reboot(ctrl+alt+delete) then just log in with the log in manager.

my systems a old vaio pcg-f430 450mhz 256ram so i always do a debian custom install and build it for speed with jwm and other lite apps.

mousepad was built on leafpad, that's why they look the same, leafpad is smaller and does not depend on anything else.

sorry it took awhile to get back to you, i have been fighting a very bad cold. :(

---

### Post by bone2006 on 2008-01-28
My system I checked on my laptop actually had 256MB of ram, but with firefox running and after a few hours the system would slow down.  I tried xubuntu and it really didn't have the speed I was looking for.

I am very happy with JWM on top of ubuntu-server.   Only about 32MB of ram is running on my system when I start up the system, then firefox adds about 75mb in total and after a long time of multitasking and playing around I barely got up to half the memory at 128mb.

So I'm really happy with the performance of having JWM installed.  Thanks for your help.

---

