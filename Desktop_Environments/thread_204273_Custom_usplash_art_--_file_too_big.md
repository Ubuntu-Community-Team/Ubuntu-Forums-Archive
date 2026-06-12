---
title: "Custom usplash art -- file too big?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Kensey on 2006-06-26
So I did up some custom art for usplash.  I created a very basic PNG with some text, set it to indexed color and let GIMP auto-generate an optimum 16-color palette, then saved it as PNG.  (I didn't edit the palette to optimize the other screen elements yet -- right now I'm just trying to get things working.)

I did pngtobogl on the PNG file, compiled the resulting C to object code and then to shared object code per the [HowTo]("http://ubuntuforums.org/showthread.php?t=82835") that was posted here, copied the resulting .so file to /usr/lib/usplash, reset the shortcut to point to my new art, reconfigured the linux-image, and rebooted.

Black screen.  Eventually I got the normal login.  This time around I went the [Wiki route]("https://help.ubuntu.com/community/USplashCustomizationHowto"), using the alternatives system.  Again, nothing kicked out an error, but I get a black screen instead of spiffy art still.

As far as I can tell I did everything correctly.  My usplash-basic.so file is very small and simple, about 28K.  If desired I can attach the original art, .c, .o or .so files in a followup.

Anybody have a remote idea what's up here?  Is there some kind of restriction on art besides the 16-color palette and the 640x400 size?

---

### Post by Kensey on 2006-06-26
Here's something interesting: when I try to boot with my custom usplash art, on the first virtual terminal I get an error message to the effect of "PCI: Failed to allocate I/O resource #7:" followed by what I assume is a memory address.  I don't get this when using the default Ubuntu or Kubuntu usplash art.  So it seems that something has gone wrong in the compilation process along the way to creating the shared object file... but what?

---

### Post by fetuszero on 2008-04-21
I get a similar problem. Followed the instructions, tried it several times so by now I assume I followed everything accordingly, yet when I boot up all I see is a black screen with a flashing underscore bar like this _ in the top left corner of the screen. Every single time the same thing happened, yet if I download a .so file from say gnome-look, it works perfectly. Anything missing in the tutorial or something? Or if anyone could give a link to something similar that has been solved because so far I couldn't find anything.

---

