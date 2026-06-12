---
title: "display mangled after viewing a video"
date: 2011-03-11
forum: Desktop Environments
---

### Post by peterballard on 2011-03-11
Hi all,

I've just watched a video (on the Australian ABC web site: [http://www.abc.net.au/news/stories/2011/03/11/3161866.htm](http://www.abc.net.au/news/stories/2011/03/11/3161866.htm) with the video at [http://www.abc.net.au/reslib/201103/r732844_5924268.asx](http://www.abc.net.au/reslib/201103/r732844_5924268.asx) ) from inside Firefox (3.0.15), and now my Linux (8.0.4) display is mangled.

The entire display is moved left and up about 2 inches on a (I think) 15 inch screen. In the vertical direction it is "wrapped" so I can still see my toolbar. It is not wrapped in the horizontal direction, so there is a black bar down the right hand side of my screen. It is as if the wrong screen size is saved.

This isn't just in my desktop environment - it goes wrong as soon as I boot into Ubuntu Linux. But my monitor itself is OK - the display is correct in GRUB and Windows.

Since the problem does not go away on reboot (or power down), I assume some file has been corrupted. Where would that file be and how would I fix it?

---

### Post by peterballard on 2011-03-11
OK, more info. 

I went into System -> Preferences -> Screen Resolution.

The screen "Monitor Resolution Settings" came up. It said:

(Inside a monitor picture): Cloned Output
Resolution: 1280 x 1024
Refresh Rate: 60 Hz
Rotation: Normal

I had no idea if these were right, but I changed the Refresh Rate to 75 Hz (this was the only option apart from 60 Hz)... and the display all came good! But I've no idea if it is safe to just change refresh rate like that. I know Windows sometimes warns you about setting the refresh rate. So... how would I find out if what I did was "safe"? I notice that when I on "Resolution" a whole lot of dimensions come up, but 1280 x 1024 is the largest. So it seems like Ubuntu has detected that my monitor's maximum size is 1280 x 1024. So... has it also detected that both 60 and 75 Hz refresh rates are safe?

---

### Post by peterballard on 2011-03-14
This isn't getting a lot of attention but I'll update anyway...

It turns out the display is still mangled (as described above) at the initial login prompt. Then when I login and enter the desktop (Gnome), my display comes good. So it seems to me some setting has been corrupted, but has been corrected (possibly in the wrong way) inside Gnome, by adjusting the refresh rate as described in my 2nd post.

So while I can live with the mucked up login screen, it'd be nice if I could know where my settings got corrupted so I can fix it properly.

---

### Post by Krytarik on 2011-03-14
I was following your thread since you started it. I don't know exactly why you have this issue, but it seems that some drivers have issues with certain video modes. For example if I set the video mode of the second monitor (LCD-TV) at my mom's machine to 60 Hz in Windows7, the display periodically gets black, every two seconds or so, 50 Hz is fine. But the same 60 Hz mode in Ubuntu does work.

If you want to apply the same mode you are using in your session to GDM's login screen, follow this guide, get the respective "xrandr" command and run it through GDM's startup script:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Greetings.

---

