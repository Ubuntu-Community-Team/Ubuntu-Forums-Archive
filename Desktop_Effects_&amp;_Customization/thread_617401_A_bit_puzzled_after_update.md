---
title: "A bit puzzled after update"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by solitary man on 2007-11-19
I'm not sure what have happened here, but somethings awry, I think.
After installing the updates in the update manager compiz isn't working any more. 
So I was wondoring if there is a way to undo those updates or if anyone knows if it something completely different that's causing the problem. 
It should probably be noted that I am currently sporting a ATI Radeon card, so I guess it's very plausible that it has something to do with that.
Any help or advice will be greatly appreciated. 

/Rasmus

---

### Post by Forlong on 2007-11-19
What's the output of ```
compiz
``` in a terminal?

---

### Post by solitary man on 2007-11-20
Here's the output from compiz.
It would appear that I no longer have Xgl.

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4150 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by Forlong on 2007-11-20
And when you install it
```
sudo apt-get install xserver-xgl
```

---

### Post by solitary man on 2007-11-28
I'm really sorry to necropost, but having been sick for the last week I haven't had the time before now.

When I install xserver-xgl everything just slows down. It reall gets very slow. So for now I've removed i again.

Rasmus

---

### Post by hbohn123 on 2007-11-28
weird

---

### Post by mcduck on 2007-11-28
I suppose you have Ati card? How did you install the drivers? And most importantly, are the drivers working correctly now?

---

