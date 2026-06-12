---
title: "GUI problems"
date: 2007-04-19
forum: Desktop Environments
---

### Post by emuellner on 2007-04-19
I just installed 7.04, I have used 6.10 in the past and had no problems. I enabled the nvidia restricted drivers, and set my resolution to 1280x1024 because I have a 19" LCD, so that's the native resolution. After I set it, my screen went blank, and did not come back for approximately 10 minutes, so I did a hard boot. Now my screen looks like this. [http://img363.imageshack.us/my.php?image=screenshotyl1.png](http://img363.imageshack.us/my.php?image=screenshotyl1.png) I am not sure what I did to cause it, or how to fix it.

---

### Post by tgm4883 on 2007-04-19
Your gonna need to bust out the digital camera to show a picture.  the screenshot you posted looks perfect.

---

### Post by emuellner on 2007-04-19
I should have specified more. My trash icon is near the middle, the volume,clock, and power symbol got switched with the other items. I also do not have correct ...border around windows. I have no close, minimize, or maximize buttons, and I can not resize them.  I hope that was descriptive enough.

---

### Post by tgm4883 on 2007-04-19
Did you enable desktop effects?

---

### Post by emuellner on 2007-04-19
No I did not. I was planning on it, but since this happened I have stopped trying to do more for the time being as to not cause any more problems, or have to do everything twice.  Is there a way to reinstall the gnome desktop without reinstalling Ubuntu that's not too complicated. I'm new to this for the most part, so I'm trying to keep things simple for now.

*update* When I try to open the Terminal, it's just a blank white window. Also if I right click on anything other than a toolbar it's just a blank white box where the list should be.

---

### Post by tgm4883 on 2007-04-19
Ok, first, did you update or install fresh.  The icon's are an easy fix.  Happens to me sometime when I resize my desktop.

Post the output of
```
 lspci 
glxinfo | grep direct
```

---

### Post by emuellner on 2007-04-19
How would I go about that if I can't access the terminal? I have tried restarting multiple times, but that hasn't changed a thing.

---

### Post by tgm4883 on 2007-04-19
ctrl-alt-f1

---

