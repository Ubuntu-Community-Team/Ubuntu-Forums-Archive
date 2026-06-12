---
title: "3d graphics problem"
date: 2005-11-21
forum: Desktop Environments
---

### Post by dsjas297 on 2005-11-21
Hello

I am running Ubuntu 5.10 on a pentium III with the intel 82810 graphics controller. Any application that I run that involves 3d grphics runs quite slow.
Any help would be appreciated.

---

### Post by Teroedni on 2005-11-21
what type of application?
Do you use a driver for your graphicscard?
like 810?

---

### Post by dsjas297 on 2005-11-22
Well, even the 3d screensavers (eg. Gears) run slow. Using the terminal, I ran "glxgears -printfps" and got some strange results. It was running at around 90 fps according to itself, but actually moving very slowly on screen.
I am not sure if any drivers are installed.
How would I check that and install new drivers if necessary?

---

### Post by dsjas297 on 2005-11-23
Can someone please help me here? I would really like to solve this problem as soon as possible.

---

### Post by Zimmer on 2005-11-23
I am not surprised the gears run slowly...
Googling for the chipset brought some interesting results..
it would seem it is an old (1999 or before) graphics controller..
see
[http://linuxgazette.net/issue52/tag/1.html](http://linuxgazette.net/issue52/tag/1.html)

and [http://support.intel.com/support/graphics/intel810/](http://support.intel.com/support/graphics/intel810/)
and here, to see how little video memory you have..(it uses the system RAM)
[http://support.intel.com/support/graphics/sb/CS-009473.htm](http://support.intel.com/support/graphics/sb/CS-009473.htm)
Is it a laptop? If not, perhaps buy a low end cheap NVidia or ATI card (check for one that is Ubuntu supported) and disable the Intel.

Zimm

---

### Post by dsjas297 on 2005-11-24
Thanks for the response. Now to find a cheap graphics card.

---

### Post by Ugeek on 2005-11-24
Try the following
           add VideoRam option to xorg.conf.
                   in the graphics driver section ; add
                              VideoRam          131072
if you have 256MB or higher Ram.
and reboot.
     you can also add your monitor's HorizSync and VertRefresh rate to monitor section in the same way for better result.

---

