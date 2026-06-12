---
title: "Changing screen res for window maker"
date: 2009-04-01
forum: Desktop Environments
---

### Post by jim.elrod on 2009-04-01
I'm using ubuntu intrepid. I just installed Window maker, but i havent been able to figure out how to change the resolution in it. I assume that it uses whatever the default resolution is for the startup screen. in my case, this is 1600x1200, which makes things just a little too tiny. I'd like it to be 1024x768. any ideas, friends?

---

### Post by mvneves on 2009-06-13
Try "xrandr -s 1024x768"

---

### Post by rustybutt on 2011-03-16
And if you're REALLY lazy like me...  you can put this into your Windowmaker menu, so you just right-click and get a selection of screen resolutions!  

At my day-job, they restrict us to using Windows on the desktop, so I run Ubuntu in a VMware Player VM and login with Windowmaker as my windowing interface.  Because I'm in a VM, I want to have a choice of window sizes.  I configured the Windowmaker menu with a selection of screen sizes.  Each selection has xrandr fired off as part of an xterm.


xterm -e xrandr -s 1440x900

for instance.  Now I just right click and get whatever resolution I want.

Much thanks to Marcelo.  I wasn't familiar with xrandr until now. Very cool.

---

