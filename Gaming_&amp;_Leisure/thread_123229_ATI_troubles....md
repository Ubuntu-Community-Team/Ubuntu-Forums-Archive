---
title: "ATI troubles..."
date: 2006-01-29
forum: Gaming &amp; Leisure
---

### Post by Klingstedt on 2006-01-29
I'm having some troubles installing ATI driver for my Radeon 9600XT 256MB
I know there is alot of guides and stuff on this forum and all that but i have manedge to install the one from ATI's homepage but i don't know if I got the right one...
I got the installer because i use Ubuntu so idont wanna mess with .rpm files.. so i downloaded this new installer and browsed to the file and typed "sh name_on_driver-8.21.7-installer.run" or whatever the name and the program starts.. i install the driver (I think) and nothing happens.. when I get a openGL and 3D-acceleration test it fails so I don't really know what the prob is...

anyone else with this problem or anyone who had it and solved it??
Would appreciate any helping answer! ;)

---

### Post by preserved on 2006-01-30
A bit more info would be appreciated.

Do you have the 32 or the 64 bits vesion of ubuntu?
And run fglrxinfo and post the results here.

---

### Post by Klingstedt on 2006-01-30
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

There's the resaults of fglrxinfo.. I have 32 bits version.

---

### Post by newuser111 on 2006-01-30
follow this guide [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

you already have the installer so it should be easy

then run sudo dpkg-reconfigure xserver-xorg and select fglrx

---

### Post by preserved on 2006-01-30
Actually I would recommend the [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)
 This one is easier...

I have tried both with my Radeon 9800 pro AIW and only this one has worked flawlessly...

---

### Post by preserved on 2006-01-30
Please do tell how it went!

---

### Post by Azmak on 2006-02-12
I have the exact same error message in regards to fglrxinfo, and this is a fresh install. Somehow this never happened with my 5.04 install. Everytime I reboot, my X config is completely screwed (No device, etc) and I have to revert to my old 'ati' drivers. I own an ATI Radeon X850.

*fglrxinfo*

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I originally tried installing the driver using the HowTo on Ubuntu's wiki, to no avail. Trying the above two walkthroughs hasn't remedied the mesa issue either unfortunately, despite the system recognising that I have an ATI card

*lspci*
> 0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4b49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4b69

According to this, [http://thinkwiki.org/wiki/Problems_with_fglrx](http://thinkwiki.org/wiki/Problems_with_fglrx), occasionally it can just be a softlink issue, but I checked everything and all of it is pointing to the right files.

Anyone have any idea of what it could be?

---

### Post by newuser111 on 2006-02-12
reading around im not entirely sure if your card works with the fglrx drivers

read around here [http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88)

and this thread [http://www.rage3d.com/board/showthread.php?t=33844819&page=2](http://www.rage3d.com/board/showthread.php?t=33844819&page=2)

---

### Post by foos on 2006-02-15
[QUOTE=Azmak]
According to this, [http://thinkwiki.org/wiki/Problems_with_fglrx](http://thinkwiki.org/wiki/Problems_with_fglrx), occasionally it can just be a softlink issue, but I checked everything and all of it is pointing to the right files.

Anyone have any idea of what it could be?[/QUOTE]

I had a similar problem. Looking around I found two versions of libGL.so.1.2, one in /usr/lib/ and another in /usr/X11R6/lib/

Copied the more recent /usr/lib/ version into /usr/X11R6/lib/ (after taking a copy, of course) and presto.

---

