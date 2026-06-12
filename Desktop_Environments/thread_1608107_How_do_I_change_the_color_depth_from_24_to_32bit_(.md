---
title: "How do I change the color depth from 24 to 32bit? (no xorg.conf)"
date: 2010-10-28
forum: Desktop Environments
---

### Post by Seeb on 2010-10-28
Hi,

since I don't have a xorg.conf anymore (just wasn't installed :-o) I wonder how to change the color depth to 32.

I'm using the standard xserver-xorg-video-radeon driver.

Thank you.

---

### Post by mcduck on 2010-10-28
You don't. :)

There is no such thing as 32-bit colors, at least when it comes to displays. Not even when Microsoft likes to call their 24-bit color mode a "32-bit" mode.

24-bit colors give you 8 bits per color channel, totaling 16,7 million colors (2^8 * 2^8 * 2^8 = ). That's way more than what most LCD displays are able to handle (in fact most consumer-grade LCD panels are really only able to display 18-bit colors)

Pictures and graphics *can* have 32-bit colors, in which case the last 8 bits are used for Alpha channel (transparency). As long as out displays can't become transparent they have no need for those last 8 bits.

edit: [http://en.wikipedia.org/wiki/Color_depth]("http://en.wikipedia.org/wiki/Color_depth")
> 
32-bit color

It is generally a misnomer in regard to display color depth. While actual 32-bit color at ten to eleven bits per channel produces over 4.2 billion distinct colors, the term &#8220;32-bit color&#8221; is most often a misuse referring to 24-bit color images with an additional eight bits of non-color data (I.E.: alpha, Z or bump data), or sometimes even to plain 24-bit data.


edit 2: if it seems like you don't have enough color depth, you are probably running in 4-bit or 8-bit color mode. In that case you can fix it using xorg.conf just like before. While the file doesn't exist by default it's used if you create it.

---

### Post by Seeb on 2010-10-28
Hey, thanks for your reply.

I already know that there is no visible difference for the human eye between 24 and 32 bit, but i think i need that 32 bit mode to get transparency with xcompmgr to work (see: [http://ubuntuforums.org/showthread.php?t=1607992](http://ubuntuforums.org/showthread.php?t=1607992) ).

I am currently running in 24 bit mode.

I will create a xorg.conf file now and I hope, Ill be able to switch to 32 bit. Thank you :-)

Edit: 
I can just "touch" the xorg.conf right? I dont have to run xorgconf, since I dont know the vsync rates and stuff from my laptop screen.

I have this now:


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    "32"
EndSection

---

### Post by mcduck on 2010-10-28
> **Seeb said:**
> Hey, thanks for your reply.

I already know that there is no visible difference for the human eye between 24 and 32 bit, but i think i need that 32 bit mode to get transparency with xcompmgr to work (see: [http://ubuntuforums.org/showthread.php?t=1607992](http://ubuntuforums.org/showthread.php?t=1607992) ).

I am currently running in 24 bit mode.

I will create a xorg.conf file now and I hope, Ill be able to switch to 32 bit. Thank you :-)

Edit: 
I can just "touch" the xorg.conf right? I dont have to run xorgconf, since I dont know the vsync rates and stuff from my laptop screen.

I have this now:


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    "32"
EndSection

no, I really mean that *there is no 32-bit mode* for your display. You can't set such mode in xorg.conf. It doesn't exist.

That's the very point of using a compositor, it composites the 32-bit graphics into 24-bit image for your display, allowing programs to use transparency.

24-bit color mode for the display is all you need, if you have problems with xcompmgr it's definitely something else than the color mode of your display.

---

### Post by Seeb on 2010-10-28
Ahh, ok, I get it.

My Xserver wouldnt want to start with those settings any way :D


thanks man.

---

