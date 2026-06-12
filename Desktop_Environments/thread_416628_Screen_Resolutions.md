---
title: "Screen Resolutions"
date: 2007-04-21
forum: Desktop Environments
---

### Post by wrm1609 on 2007-04-21
I'm an experienced Windows user, but novice Linux user who has just installed Ubuntu 7.04. Impressed with all I have seen so far, but have a problem.

I have a Hanns-G  HW191D widescreen monitor running on a ASUS Extreme AX300 Series graphics card. In Windows this runs at 1440x900 resolution. In Ubuntu, I am offered no choice of wide screen resolutions, with the result that everything on screen looks stretched. I have installed the ATI restricted drivers. 

Haven't been able to find anything on the forums that tell me how to resolve this. Can anyone help?

Thanks

---

### Post by Turgon on 2007-04-21
If you search for screen resolution, im sure you will find a solution for this (its a common problem)

Anyway, what you need to do is to add the desired resolution into the xorg.cof file. This can be done by doing it automaticly or by reconfiguring xorg.conf via the terminal by using this command:

sudo dpkg-reconfigure xserver-xorg

This wll start a wizard where you configure video-card (choose the fglrx driver for the ati driver), keyboard, mouse and screen. Mostly you can just puch enter, but read what it says anyway. When its time to choose resolutions, just add the desired resolution  by pressing space. Finish, then restart your X-server by pressing Ctrl-Alt-backspace (or just do a simple restart)

Good luck!

---

### Post by wrm1609 on 2007-04-21
Did as you suggested, and all is now well. I will get the hang of Linux, or die in the attempt !!

Thanks for your prompt help.

---

