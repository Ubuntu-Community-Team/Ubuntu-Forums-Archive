---
title: "desktop effects do not work at resolutions above 1024x768"
date: 2007-06-26
forum: Dell  Ubuntu Support
---

### Post by nithska on 2007-06-26
_Issue:_ 7.04 'desktop effects' do not work at resolutions above 1024x768.  They do work just fine at 1024x768.  This laptop can handle resolutions up to 1400x1050 which works fine when desktop effects are not enabled.  When desktop effects are enabled at 1400x1050, the right third of the screen fills with screen artifacts while the remaining area corresponding to 1024x768 (I speculate) remains viewable.
_Specs:_
Dell D600
32MB ATI Mobility Radeon 9000, no additional restricted driver installed (restricted driver manager reports that none are needed)
Ubuntu 7.04, fresh install: no additional desktop effects options installed (beryl, fusion, etc.)

Note that there is another post under desktop effects where a user with an Acer laptop is seeing ther same issue, so I suspect there is a file that just needs to be edited so that the desktop effect can work with the higher resolutions.   Also, I want to solve this problem, not install fusion or beryl.   I'm trying to keep this as default as possible.

Thank you,

B.

---

### Post by nithska on 2007-06-27
bump

---

### Post by Steveway on 2007-06-27
This could be connected with the maximum texture size.
Could you post the output of glxinfo here?

---

### Post by steve.horsley on 2007-06-27
I have a latitude D600, and apparently the maximum texture size on the ATI video controller is 1024x1024. Disappointing. But you can't blame Ubuntu for dell putting under-specced hardware in the box.

---

### Post by nithska on 2007-06-27
That is disappointing.  I don't guess there's any work-around for this?  I'll probably opt for the higher resolution with no effects than go back to 1024x768.

Thanks for the help,

B

---

### Post by technikalKP on 2007-06-27
modify the xorg.conf file and set Default Color Depth = 16.  It's probably set to 24  now.  Reboot and desktop effects should work fine at full resolution.

The 32mb ATI card in the D600 doesn't have enough memory to handle everything at full bit depth.  Drop it down to 16 bits and everything should work fine.  You will give up a bit of image quality due to the lower number of colors, but the effects are worth it, imo.

---

### Post by rivasdiaz on 2007-06-27
Are you sure this is not a video driver problem?

I have Ubuntu 7.04 with 1680x1050 on an Intel video based dell laptop and the desktop effects works ok.

---

### Post by s1ightcrazed on 2007-06-27
My guess is that your intel (like mine) uses shared memory, so as long as you have fed it enough it will work fine. I'm surprised the ATI card can't fall back to shared memory, but on board chipsets do weird things sometimes, so who knows.

---

### Post by caro on 2007-06-28
I have a Dell e1505 with the Intel onboard graphics, 512Mb RAM, and I am able to use Desktop effects with 1280x800.

---

### Post by mordani on 2007-08-16
Here is something interesting that I did. I downloaded 915resolution and my laptop (Dell Inspiron 1420)  had the correct resolution of 1440x900 (Exactly what I wanted). However, the desktop effects were not working no matter what I did.  

Eventually I figured that the driver entry was not updated in /etc/X11/xorg.conf and the device entry was still ¨vesa¨. I changed this to ¨i810" and then the enabled desktop effects - now it works perfectly !!

~Rohit

---

### Post by zachtib on 2007-08-27
> **mordani said:**
> Here is something interesting that I did. I downloaded 915resolution and my laptop (Dell Inspiron 1420)  had the correct resolution of 1440x900 (Exactly what I wanted). However, the desktop effects were not working no matter what I did.  

Eventually I figured that the driver entry was not updated in /etc/X11/xorg.conf and the device entry was still ¨vesa¨. I changed this to ¨i810" and then the enabled desktop effects - now it works perfectly !!

~Rohit

there's a way to fix this, i've done it in the past, and i'm searching for it now.  the problem is the max_texture_size, but i can't remember the name of the app that lets you configure it

UPDATE: it's called driconf, and you have to use it to enable large texture support, testing now

UPDATE2: yep, it worked.  go into the expert mode of driconf and enable support for textures that may not fit in available video memory, save, then restart X

---

