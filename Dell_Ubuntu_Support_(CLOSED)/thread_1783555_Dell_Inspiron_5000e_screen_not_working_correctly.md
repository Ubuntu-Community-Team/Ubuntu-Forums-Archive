---
title: "Dell Inspiron 5000e screen not working correctly"
date: 2011-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by The Silence on 2011-06-15
Hello, this is my first post, so please excuse anything that is terribly misspelled, blatantly ignorant, etc.

I recently installed Ubuntu version 11.04 onto my Dell Inspiron 500e, and my screen has been distorted. The first half (going left to right) of the screen appears normal, and at the halfway point, there are about four vertical bars tat will all display different parts of the screen, followed by a black bar, and a repetition of the Rightmost portion of the screen. This means I basically only have half a screen, plus the very end of the top bar. ( sorry for my lack of technical terms: I mean the bar along the top of the screen with "Applications; Places: System". When i move my cursor into this area it is also repeated. I have tried numerous times to change the display size using ```
xrandr --newmode
xrandr --addmode
``` (and several others using xrandr) but each time I was met with "Could not get gamma for default", and all the other suggestions on the Internet involve a version of ubuntu no later than 7.04. So I would be grateful for any and all suggestions. 

Thanks

---

### Post by grusso on 2011-11-29
I have the same problem.  It has something to do with the LCD display not being properly recognized.  I fixed it in a previous version of Ubuntu using the xorg.conf file, but I recently wiped out the hard disk and did a clean install of version 11.10 and I forgot what I did.  So now I'm back trying to figure it out.  When I do, I'm going to put that xorg.conf file in a safe place!

---

### Post by grusso on 2011-12-09
Here is the xorg.conf file that works on my Inspiron 5000e.  Remove the .txt extension, then copy it to your \etc\X11 directory and reboot.  You may need superuser privileges to copy into that directory.  Good luck.

---

### Post by Jones235 on 2012-01-31
> **grusso said:**
> Here is the xorg.conf file that works on my Inspiron 5000e. Remove the .txt extension, then copy it to your \etc\X11 directory and reboot. You may need superuser privileges to copy into that directory. Good luck.
 
Will this file work with an Inspiron 8000?:-s

---

### Post by AdheringComic on 2012-04-05
Thanks for the config file, grusso. Did the trick and fixed the flicker / overlap issue on my OAP 5000e! Very pleased with Ubuntu bringing it back to life!! :p

---

