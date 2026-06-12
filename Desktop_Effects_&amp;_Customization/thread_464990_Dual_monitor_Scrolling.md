---
title: "Dual monitor Scrolling"
date: 2007-06-05
forum: Desktop Effects &amp; Customization
---

### Post by Seeker84 on 2007-06-05
I've managed to get dual monitor to work on my laptop to a LCD screen.  My Issue I'm having is that the LCD screen needs to scroll to get to the edges. Does anyone have a solution for this using a Intel graphics card?

---

### Post by Soybean on 2007-06-05
This usually means that you've set the resolution higher than what your monitor can handle. Alternately, it may mean that you've set the resolution higher than what X *thinks* your monitor can handle. ;) 

If you need more specific advice on how exactly to fix it, I'd recommend posting your xorg.conf and a bit more info about your monitors. I don't think I'll be around much more today, but someone should be able to help. :)

---

### Post by Seeker84 on 2007-06-05
Well that fixed the scrolling issue.  My external was set to 1280x800 when it could go 1280x1024.  So all I did was changed the modes to 1280x1024 on my external and I was good to go.

the way I found out was that the monitor is currently hooked up to an xp machine.  right clicked screen>properties>settings>click the second monitor you are trying to use>look at screen resolution.

---

