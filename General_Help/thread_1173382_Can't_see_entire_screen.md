---
title: "Can't see entire screen"
date: 2009-05-29
forum: General Help
---

### Post by dbyjazz on 2009-05-29
I can't see my entire screen, only a very small portion. (laptop)

This is what my screen should look like (I can move my mouse beyond what my monitor shows)

[IMG]http://i272.photobucket.com/albums/jj165/dby12/Screenshot.png[/IMG]

and this is all that I can see

[IMG]http://i272.photobucket.com/albums/jj165/dby12/Screenshot-1.png[/IMG]

If I change the screen resolution, my screen turns to this...

[IMG]http://i272.photobucket.com/albums/jj165/dby12/0528091226_01.jpg[/IMG]

and the only way I can get my screen to look like picture 2 again, is if I reinstall Ubuntu 9.04

If anyone can help me I would greatly appreciate it. I have had this problem for some time.

---

### Post by ghindo on 2009-05-29
Do you have an Nvidia or ATI graphics card?

---

### Post by dbyjazz on 2009-05-29
> **ghindo said:**
> Do you have an Nvidia or ATI graphics card?

I don't know. I'm a n00b at this :/

---

### Post by ghindo on 2009-05-29
> **dbyjazz said:**
> I don't know. I'm a n00b at this :/That's okay.  What kind of computer do you have?  Please describe in as much detail as you can.

---

### Post by dbyjazz on 2009-05-29
> **ghindo said:**
> That's okay.  What kind of computer do you have?  Please describe in as much detail as you can.

Gateway NX260X
[IMG]http://laptoping.com/wp-content/gateway_m255e.jpg[/IMG]

Processor: Intel Celeron M Processor 370
Operates at 1.5 GHz, 1 MB L2 Cache
and 400 MHz FSB

Memory: 512 MB DDR2

Video: S3 Graphics UniChrome Pro IGP
As much as 64 MB shared VRAM

Hard Drive: 60 GB HDD, 4200 RPM

---

### Post by ghindo on 2009-05-29
Okay, so it looks like you have Intel integrated graphics.  When did this problem start?  Do you know what started it?

---

### Post by dbyjazz on 2009-05-29
> **ghindo said:**
> Okay, so it looks like you have Intel integrated graphics.  When did this problem start?  Do you know what started it?

I was previously running Windows XP. There were no problems with the screen then, but then I switched to Ubuntu, and that's when it happened.

---

### Post by Yellow Pasque on 2009-05-29
Sounds like a faulty virtual screen size. This is a common issue with the version of the openchrome driver included with Jaunty. Please attach /var/log/Xorg.0.log

FYI: S3 graphics is not Intel graphics; it's VIA graphics.

---

### Post by dbyjazz on 2009-05-29
> **Temüjin said:**
> Please attach /var/log/Xorg.0.log

xorg

---

### Post by Yellow Pasque on 2009-05-29
First, try using the latest video driver: [http://packages.ubuntu.com/karmic/i386/xserver-xorg-video-openchrome/download](http://packages.ubuntu.com/karmic/i386/xserver-xorg-video-openchrome/download)

If that doesn't work, edit your /etc/X11/xorg.conf file to manually specify the virtual screen size:
```
gksudo gedit /etc/X11/xorg.conf
```

Add a block like this to the "Screen" section:
```
Subsection "Display"
    Depth 24
    Modes "1280x800"
    Virtual 1280 800
EndSubsection
```

---

### Post by dbyjazz on 2009-05-30
I'll try it. Thanks

---

### Post by dbyjazz on 2009-05-30
It worked! Thank you so much bro.

Here's an E-cookie :)

[IMG]http://pixiestixkidspix.files.wordpress.com/2007/08/cookie-bite-web.jpg[/IMG]

---

### Post by Yellow Pasque on 2009-05-30
Thanks for the cookie. For the sake of posterity, did installing the new driver fix it, or did you also have to hack the xorg.conf?

---

### Post by dbyjazz on 2009-10-21
the xorg.conf is what did the trick

---

### Post by karlmp on 2009-11-05
thank you!:KS

for some reason that doesn't work for kde but works for lxde

UPDATE:and the screen is going white in lxde...

---

