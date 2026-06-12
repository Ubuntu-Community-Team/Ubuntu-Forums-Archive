---
title: "Wallpaper changer with some extras"
date: 2009-12-30
forum: Desktop Environments
---

### Post by mikeliketrike on 2009-12-30
I've recently built a digital photo frame using Ubuntu and keeping Gnome as my desktop environment.  Everything's working great on it and glScreensaver does what I need it to do.  
But I want to keep playing with it.  
I want to add extras that other people's digital photo frames don't have.  Screenlets would let me do that pretty easily, but they're behind glScreensaver and Feh when it runs in full screen slide show mode.

My thought is that I'd hide all the "regular" stuff on the desktop (icons, cursor, panels) and just change the wallpaper every 10 seconds or so.  I'll throw a screenlet clock and maybe the weather on there and it'll be awesome.

Is there a program/script that will allow me to recursively pick a random wallpaper (I've got 17k+ pictures) from a directory every x seconds?

Feh's the first thing that came to my mind, but I don't know how to make it do what I want it to.

Thanks!

---

### Post by .nedberg on 2009-12-30
In KDE4 you can select a folder to use for a slideshow... Not sure if it works recursively as I have never tested it. KDE4 also has "screenlets"!

---

### Post by nilarimogard on 2009-12-30
Try Desktop Drapes (sudo apt-get install drapes) or this script: [http://ubuntuforums.org/showthread.php?t=1344787](http://ubuntuforums.org/showthread.php?t=1344787)

---

### Post by Gourgi on 2009-12-30
```
sudo apt-get install wallpaper-tray 
```
;)

---

### Post by mikeliketrike on 2009-12-30
> **Gourgi said:**
> ```
sudo apt-get install wallpaper-tray 
```
;)

Woo hoo!  Wallpaper try it is.  It works perfectly.  

So if anyone reading this after searching for something like diy digital photo frame or linux photo frame, use wallpaper tray.  Use it instead of feh or a screensaver, it does the same function (rotates through pictures) but gives a lot more functionality.  

I don't know if there's a tutorial spot in Ubuntu forums but using wallpaper tray along with screenlets to make an "above average" digital photo frame should be included.

---

### Post by Gourgi on 2010-01-02
glad you liked it , i use it too and it is just perfect for its purpose.
it should be included as default IMHO.

---

### Post by mikeliketrike on 2010-01-02
It's perfect for a digital photo frame, the only thing I don't like about it is it's a little CPU heavy.

---

