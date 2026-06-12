---
title: "XGL + FVWM = b0rkd!"
date: 2006-03-04
forum: Desktop Environments
---

### Post by linkunderscore on 2006-03-04
I installed xgl and compiz to get the sweet effects in gnome, but I really enjoy messing with my fvwm configs when I get bored. Unfortunately fvwm doesnt really support xgl very well. I get missing pagers, blacked out menus and consoles, etc. 

I have gdm set up to start with xgl, so I figured the best way around xgl would be to stop gdm and "startx fvwm"... this works-sort of. 

It starts fvwm normally (through regular X) and everything works great, BUT I cannot open any terminals(xterm,urxvt,gnome-terminal, aterm, eterm, etc)...at all. They pop up then disappear very quickly. 

My questions are:
Does anyone know how to run fvwm with xgl? 
Does anyone know how to set-up gdm to use xgl for gnome, but use regular X for fvwm?
If none of the above can be accomplished, does anyone know how to fix my terminal issues?? 

Thanks in advance!

edit: I am still running Breezy. I just installed the appropriate .debs to allow me to use xgl and compiz. But I am not sure if this thread is in the appropriate forum. Admins, you can move this to the Dapper forums if you deem necessary.

---

### Post by ThomasAdam on 2006-03-05
[QUOTE=linkunderscore]Does anyone know how to run fvwm with xgl?[/quote]

Whilst XGL is at the X11 layer, there is still some WM interactivity that needs to take place in order for some of XGL's effects to be used.  Given that XGL is a relatively new release, and that FVWM's development focus is currently elsewhere (I've likely alluded you to this on other forums), it's unlikely to have XGL support at the moment.

-- Thomas Adam

---

### Post by linkunderscore on 2006-03-07
YOU ARE EVERYWHERE!!!! :) :) 


Well, I was just hoping someone on here knew of a work around.

---

### Post by jpkotta on 2006-03-17
If X + Composite is an option, then I have a mostly-stable configuration with FVWM, xcompmgr, and nvidia drivers 1.0-8178.  I am waiting to try Xgl until Dapper is released.

---

