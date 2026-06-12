---
title: "screen resolution"
date: 2007-03-23
forum: Desktop Environments
---

### Post by bearcat on 2007-03-23
Here's the deal: every time I boot into Ubuntu, I get a warning that I'm not at optimum display size; it recommends 1440x900. However, if I actually set my resolution to 1440x900, the result is that my desktop ends up wildly misaligned to the actual screen, and no amount of manually adjusting the display fixes this. I'm currently on 1280x1024, which works fine.

So my question is, how can I either (a) get 1440x900 to work right, or (b) make Ubuntu stop telling me to change the resolution?

I'm using Edgy, but I had the same problem when I was using Dapper.

---

### Post by swamytk on 2007-03-23
Ensure that the Horizontal Sync and Vertical Refresh values are as per monitor spec.
If you are using Generic CRT/LCD Monitor, Ensure that you have selected resolution of monitor as 1440x990.

---

### Post by J77 on 2007-03-23
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

You may also need the prog. 855resolution  -- I remember for my laptop I had to change one of the default available resoltuions to my desired high-res (also have to do this for widescreen) and write a startupscript which ensured the change on each boot.

e2a: here you go [http://ubuntuforums.org/archive/index.php/t-24923.html](http://ubuntuforums.org/archive/index.php/t-24923.html)

---

### Post by bearcat on 2007-03-23
This helped to an extent, but the bottom panel is still positioning below the bottom of my actual display area in 1440 mode. And yes, I've double-checked the sync values to ensure that I entered them correctly.)

So I guess now my question is how do I force the bottom panel up?

---

### Post by J77 on 2007-09-17
Right-click on the panel and go to properties, then orientation.

---

### Post by olieviya on 2007-09-17
Do you have the newest driver for your graphics card installed?
Make sure the drivers are all working ok and are up to date also you might want to try reinstalling them even if they are the newest version.

---

