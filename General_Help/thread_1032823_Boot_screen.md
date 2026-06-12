---
title: "Boot screen"
date: 2009-01-06
forum: General Help
---

### Post by hoboboot on 2009-01-06
[SOLVED] - cant get 1280x768 but 1280x1024 works, and it works in a manner that is not low resolution, AND not off the edge of the screen (aka scaled to fit) 
thanks guys!

I got my resolution issue corrected from being way too big for the display, to, just a perfect fit [1280x768] for the screen...but i was wondering if anyone could help me fix my boot screen resolution? this image here is the screen i'm referring to, so as there is no confusion... 

[IMG]http://lirent.net/wp-content/uploads/2008/05/boot-screen.jpg[/IMG]

anyway i'd like to be able to change that from being too big running off the display's edges resolution to, perfect fit 1280x768 too. im a perfectionist when it comes to my computer and i cant live with details like this when i know it can be fixed... problem is i dont know where that information is , so ... someone kindly help me out?

---

### Post by skern03 on 2009-01-06
> **hoboboot said:**
> I got my resolution issue corrected from being way too big for the display, to, just a perfect fit [1280x768] for the screen...but i was wondering if anyone could help me fix my boot screen resolution? this image here is the screen i'm referring to, so as there is no confusion... 


anyway i'd like to be able to change that from being too big running off the display's edges resolution to, perfect fit 1280x768 too. im a perfectionist when it comes to my computer and i cant live with details like this when i know it can be fixed... problem is i dont know where that information is , so ... someone kindly help me out?

Load an app called startupmanager. It's a grub and splash screen manager. You can set the resolution with it. See attached image.

You can load it via Syanptic Package Manager by searching for the word (no spaces) startupmanager, or in a terminal with

> sudo apt-get install startupmanager

---

### Post by Shazaam on 2009-01-06
You can add either a vga= to the end of the grub kernel line or install Startup Manager from the repos (Synaptic). A vga example is this...
```
vga=784
```
from this...
```
Color depth      | 640x480 | 800x600 | 1024x768 | 1280x1024
-----------------+---------+---------+----------+----------
256 (8bit)       |   769       771       773        775
32000 (15bit)    |   784       787       790        793
65000 (16bit)    |   785       788       791        794
16.7 Mill.(24bit)|   786       789       792        795
```
Another way using decimals....
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

