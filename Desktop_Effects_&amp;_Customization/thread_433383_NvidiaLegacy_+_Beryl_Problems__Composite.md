---
title: "NvidiaLegacy + Beryl Problems : Composite"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by Pox on 2007-05-04
Hey all :)

My sister's been wanting linux for a while after seeing my setup, so I've gone ahead and installed xubuntu 6.10 on her machine and updated it to feisty straight away.  (Yeah, I know, ISO would have been easier, but couldn't be bothered downloading + burning another disk.)

For reference, here's the specs:

AMD Athlon XP 1900+
768MB RAM
64MB Nvidia mx400

So far, all's gone perfectly smoothly - installed fine, updated fine, and I got the nvidia-glx-legacy installed easily.  GLX Extension is working perfectly and Enemy Territory (her main concern XD) is running smoothly.

She's now asking for Beryl.

I attempted to go ahead and install 0.2 from Synaptic - it installed fine with no errors, and beryl-manager is showing up in the apps menu.

However, when I try to start it through beryl-manager, it complains there's no Composite extension available.

OK, so I knew what was wrong there - Composite was disabled.  I vimmed her xorg.conf and changed the "Disable" to "Enable" for the Composite option.

Didn't work.  Enabling Composite seems to have broken the glx - I now get

```
Xlib: extension "GLX" missing on display ":0.0".
```

when I try to start Beryl, glxgears or any other 3d-accelerated program.

I know it's possible to run Beryl on a mx400, I've seen it done... not sure what's wrong.

For reference, the nvidia-glx-legacy is installing version 7184... this seems quite old to me.  I know my Geforce6 needs the nvidia-glx-new package (9755), so I'm wondering if 9631 would work.. don't want to break anything though.  Also, the mx400 _is_ a Geforce2 card, which is listed under the legacy section.

Any ideas? Anyone else got Compositing running on a Geforce mx4xx?

Thanks in Advance for any help :)

---

### Post by allwin on 2007-05-05
Yes, the 9631 works for my card.  I used ENVY to install the driver, but then had to sprinkle in the xorg.conf changes to turn on composite, etc, manually.  Eventually you'll get it right if you check the various posts around here.  While I was at it, I had to address the screen resolutions and ignore EDID option so my keyboard video monitor switch would work properly.  I have that stuff in my conf...don't want to post it or it'll confuse you!  If ENVY doesn't install the driver you are SOL, it's apparently smart enough to know which card matches which driver.  Google for "ENVY nVidia" and you will find it.  Don't know what the latest release is.  BTW, ENVY works from the console in case your desktop is blown away and you don't know what to do, once it's installed "sudo envy" and away she goes.  You'll HAVE TO RUN ENVY every time there is a Linux kernel update too!  Get used to it.

---

### Post by allwin on 2007-05-05
Oh and I forgot YOU WILL PROBABLY GET BLACK WINDOWS!  You'll see what I mean soon enough if you have an old nVidia card!  It's a driver problem (remember Beryl is beta code and so is the driver).  Heh, what do you expect for the price.  If you see black windows once you get Beryl running, resizing the window smaller usually brings it back to visible, if you can physically do that (some times you can't).  Plenty of snake oil remedies out there.  Google or search this forum for plenty of tricks you can try if (I mean WHEN) this happens to you.  Still with the latest Beryl, it's not so bad, about every fifth window for me, or sometimes the entire desktop is black upon login.  Restart Beryl window manager cleans things up most of the time.

Oh, and WHEN RUNNING UPDATE MANAGER...remember to turn Beryl off, or when doing something critical where you, like, have to see the window.  Enjoy.  Still worth it for the wiggle.

---

