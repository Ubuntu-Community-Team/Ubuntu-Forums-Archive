---
title: "Ubuntu hooked up to HDTV cuts off left half of screen"
date: 2012-09-07
forum: Desktop Environments
---

### Post by aidenkael on 2012-09-07
I have Ubuntu hooked up to a 40" HDTV through a VGA to VGA connection.  About half the screen is cut off on the HDTV however.  Anyone know an easy fix?  I want to Mirror the desktop to the HDTV and us it as my only monitor.

---

### Post by SeijiSensei on 2012-09-07
What kind of video card do you have?  Does it have a DVI connector as well as VGA?  If you use a DVI-to-HDMI cable to connect to an HDMI port on the TV, does that work?

I have a Sony Bravia connected to a XFX graphics adapter with an NVIDIA 9500GT.  I can connect to the TV with both VGA and DVI. I'm looking at that very screen right now as I type.

---

### Post by aidenkael on 2012-09-08
> **SeijiSensei said:**
> What kind of video card do you have?  Does it have a DVI connector as well as VGA?  If you use a DVI-to-HDMI cable to connect to an HDMI port on the TV, does that work?

I have a Sony Bravia connected to a XFX graphics adapter with an NVIDIA 9500GT.  I can connect to the TV with both VGA and DVI. I'm looking at that very screen right now as I type.

I have ubuntu on an asus eeepc, so I only have the VGA port.

---

### Post by SeijiSensei on 2012-09-08
I have an eeePC 1201n which has an NVIDIA card.  (I bought this model precisely to have an NVIDIA adapter.)  It's also from the days before Optimus so it's the only adapter in the machine.  I also run Kubuntu 12.04.  So, as they say, YMMV.

As a test, I connected the ASUS to my TV over VGA.  The default display application in KDE didn't detect the TV, but the proprietary NVIDIA application did.  I told it to use the TV as the output, at which point it restarted the X server, and the normal display appeared correctly on the TV.

Switching between displays using Fn-F8 didn't seem to work at all.  I had to use the software display manager itself.  Once I did that, though, I had no problem putting the full 1920x1080 picture on the screen.

However my Sony Bravia offered three different screen resolutions for the VGA signal -- normal, "wide 1" and "wide 2".  The first was 4:3 rather than 16:9.  The second put the display in a black box on screen, but the last one displayed it fullscreen.

So I can suggest trying:

1)  Play with the widescreen settings on the TV.  Maybe you just need to put it into a different mode.

2)  Try using the configuration tools and perhaps the xrandr application to move the display onto the TV and resize it appropriate.  On my system xrandr is called "Screen Rotate and Resize" and appears in the System menu.

---

### Post by aidenkael on 2012-09-08
> **SeijiSensei said:**
> I have an eeePC 1201n which has an NVIDIA card.  (I bought this model precisely to have an NVIDIA adapter.)  It's also from the days before Optimus so it's the only adapter in the machine.  I also run Kubuntu 12.04.  So, as they say, YMMV.

As a test, I connected the ASUS to my TV over VGA.  The default display application in KDE didn't detect the TV, but the proprietary NVIDIA application did.  I told it to use the TV as the output, at which point it restarted the X server, and the normal display appeared correctly on the TV.

Switching between displays using Fn-F8 didn't seem to work at all.  I had to use the software display manager itself.  Once I did that, though, I had no problem putting the full 1920x1080 picture on the screen.

However my Sony Bravia offered three different screen resolutions for the VGA signal -- normal, "wide 1" and "wide 2".  The first was 4:3 rather than 16:9.  The second put the display in a black box on screen, but the last one displayed it fullscreen.

So I can suggest trying:

1)  Play with the widescreen settings on the TV.  Maybe you just need to put it into a different mode.

2)  Try using the configuration tools and perhaps the xrandr application to move the display onto the TV and resize it appropriate.  On my system xrandr is called "Screen Rotate and Resize" and appears in the System menu.


Tried both your suggestions and the first one was a no go.  The second one was also a no but only because I couldn't find any of the things you mentioned.  I searched for xrandr and I don't have it, but I did find a Display option which I played around with for a while to no avail.  I am using Ubuntu 12.04 if that helps.

---

### Post by aidenkael on 2012-09-09
bump

---

### Post by aidenkael on 2012-09-10
Figured it out!  I needed to go into my TV's setting and change the "computer settings".  The key was that this specific group of settings only appeared under "system", and not "picture, and also only appeared when it detected the VGA connection.  Cheers for the help all!

---

### Post by SeijiSensei on 2012-09-10
Great!  I suspected the TV was the culprit.

---

