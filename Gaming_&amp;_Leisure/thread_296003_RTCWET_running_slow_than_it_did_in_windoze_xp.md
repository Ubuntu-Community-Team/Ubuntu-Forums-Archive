---
title: "RTCW:ET running slow than it did in windoze xp"
date: 2006-11-09
forum: Gaming &amp; Leisure
---

### Post by Junk_head on 2006-11-09
Hello ubuntu community, im a noob at linux and decided to do the switch, so far i've been happy, but than i wanted to play EnemyTerritory, like on XP, but it seems like everything was slow, I tried lowest settings and everything was still going slow. I'll post my specs here:
Intel Celeron 1.7ghz
Intel Intergrated Graphic
384mb of ram
not exactly state of the art but neither is Enemy territory
anything that might help? :(

---

### Post by hikaricore on 2006-11-09
You might want to check to see if direct rendering is enabled in a terminal.

```
glxinfo | grep rendering
```

This should output a yes.

Also are you using an ATI or onboard intel type video card?  These cards suffer slightly in the Xwindow system depending on your configuration and what you are trying to run.

And last if you have any type of Nvidia graphics card you need to install the drivers for your specific card or you won't get the performance you've come to expect.

You may even need to fine turn your video settings in the game slightly to get optimal performance.

I know things are a little different here, but if you can get everything running smoothly, I'm sure your computing experience will be much more enjoyable without the pitfalls of windows.

Good Luck,

--Aaron

---

### Post by hikaricore on 2006-11-09
One more thing I forgot >.<

In the "Screen" section of your xorg.conf file (located at */etc/X11/xorg.conf*)

try changing the line that says **Default Depth**, which may be at 24, to the number 16.  It may help your situation, I notice things are 10x as fast with 16bit color on my system.

To do this enter:

```
gksudo gedit /etc/X11/xorg.co**n**f
```

what you're looking for should look something like this:

> Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        _DefaultDepth    16_

If it's already at 16 leave it be, but if it's at 24 try chaning it then save the file.

Logging out of X and back in will reread these settings.

---

### Post by Junk_head on 2006-11-09
My card showed yes to the first post but the 2nd fix couldnt be done 
Seems like my xorg.cof is blank ](*,)

---

### Post by hikaricore on 2006-11-09
Sorry dude, my typo >.< it's **/etc/X11/xorg.conf**

I left off the "n" in conf

---

### Post by Junk_head on 2006-11-09
I tried the 16 bit but alas i'm still getting slow down, although i noticed my card was called Generic Card instead of Intel maybe the drivers are wrong

---

### Post by hikaricore on 2006-11-09
> **Junk_head said:**
> I tried the 16 bit but alas i'm still getting slow down, although i noticed my card was called Generic Card instead of Intel maybe the drivers are wrong

It doesn't matter what your card is called, just what driver it's using.

If you're using the i810 chipset there's an updated driver posted around here somewhere that fixes some issues.

Also did you restart after you changed the line to 16 bit?

---

### Post by Junk_head on 2006-11-09
Yes i restart the game got a little faster but still some slow down  and it seems the guns have a vomit texture going on from the 16-bit depth. I;l look for the driver around
If any help the card is intel 845
and im running edgy ubuntu

---

### Post by hikaricore on 2006-11-10
The vomit texture issue sounds like the same problem I'm having on an MGA video card that I have here at the office, I don't think there's much of a solution for this just tweak the game settings and make sure they're set at low and set to use 16bit color as well.  Once you get it looking nice you can test increasing different video features until you're satisfied.  I was personally unable to find the updated driver I mentioned but just search around the board for: i810 edgy

I'm fairly certain you're using that driver.

Hope you figure it out, and I'm glad 16bit is speeding things up a bit.  :)

---

