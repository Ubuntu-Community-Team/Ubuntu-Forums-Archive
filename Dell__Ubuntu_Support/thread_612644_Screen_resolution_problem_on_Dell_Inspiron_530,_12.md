---
title: "Screen resolution problem on Dell Inspiron 530, 128MB NVIDIA GeForce 8300GS"
date: 2007-11-14
forum: Dell  Ubuntu Support
---

### Post by steved on 2007-11-14
Here's the problem I'm having with a Dell computer I'm setting up for an in-law:

Dell Inspiron 530
128MB NVIDIA GeForce 8300GS
1440x900 17 inch SE178WFP Widescreen Flat Panel Monitor 
Ubuntu 7.04

In Ubuntu's screen resolution settings, the max screen resolution I have on this 1440x900 res monitor is 1024x768. So my picture is stretched and not crisp.

My questions
============
My first question is: Are the drivers for my video card already on my hard drive and available to Ubuntu or do I have to download them from Dell? I received an NVIDIA disk with my shipment but it only has Windows drivers on it.

If the driver is already installed, can someone please tell me definitively what I need to do to get things working properly? There is no Internet connection for this computer at my in-law's house and so I need a procedure or link to a procedure that will **absolutely, positively** work for this particular Dell hardware configuration so I can print it out. I'd hate to go all the way there, try something, and then have it not work.

P.S. I work with Debian computer's from the command line all the time but I'm not familiar with x11 or Linux driver configuration files at all.

Dell rant, safe to ignore
===============
I had sworn off ever buying or recommending Dell but when I wanted to set my in-law up with a low maintenance Linux computer, I decided to go against my better judgment to save me the hassle of worrying about hardware compatibility and downloading and configuring Ubuntu by myself. My time is very short these days. I figured Dell would have everything perfectly configured for the hardware and everything would work perfectly out of the box. Wrong! I also figured that if there were any technical support issues, I could get help from them instead of spending hours googling and asking questions...but here I am!

Me to Dell tech person on the other side of the planet after telling them twice already I'm using Ubuntu: "I can't click 'Start', I'm using Ubuntu." So after supposedly transferring me to their Ubuntu department which turned out to not be the Ubuntu department after all, I gave up.

---

### Post by RTrev on 2007-11-14
You should be able to use the "Restricted Drivers Manager", which is under the System | Administration menu, to see what driver is available to you and to install it.

Next step.. reboot

The silly Restricted Driver Manager will now notify you that you have a new driver (duh) and you have to click an acceptance button.

Finally, get back to a command line, and run this:

```
sudo dpkg-reconfigure xserver-xorg
```

Make sure you choose the correct resolution for your setup.. that is, the one you want to be using (1140x900).  No need to select any but the one you want.

Final step.. Ctrl-Alt-BackSpace .. and up should come your newly configured X system.

Bob

---

### Post by Dellfan on 2007-11-14
There is an official Dell Ubuntu support team. The number for the US is 1-866-622-1947. They definitely can assist with issues on Dell's shipped with Ubuntu. Anyone you get in Dell Support should be able to route you correctly to these folks but that does not always seem to happen. Try calling them directly.

Likely you can resolve your issue by enabling the restricted Nvidia driver and perhaps tweaking xorg.conf.

---

### Post by steved on 2007-11-14
OK, Thanks! I'll try it out this weekend and report back my results to the rest of humanity.

---

### Post by steved on 2007-11-25
Problem resolved. See my post at [http://ubuntuforums.org/showthread.php?p=3836324#post3836324](http://ubuntuforums.org/showthread.php?p=3836324#post3836324)

---

