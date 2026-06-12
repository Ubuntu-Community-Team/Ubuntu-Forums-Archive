---
title: "gnome-panel always crashes in Jaunty"
date: 2009-05-10
forum: Desktop Environments
---

### Post by HCF1 on 2009-05-10
Hi everyone,

yesterday I upgraded from Ubuntu 8.10 to 9.04 (32bit, installation without any problems). But since the first start of Jaunty, the panel (gnome-panel) keeps crashing. 

Trying to start gnome-panel in a terminal results in the following error (beside some warnings regarding libglade, that are ignored): 
> gnome-panel: symbol lookup error: /usr/lib/gnome-panel/libclock-applet.so: undefined symbol: gtk_orientable_get_typeI found out that this file is used by the clock applet, but I can't prevent it from being started by gnome-panel. Is there any way to manage that?

I tried to reinstall gnome-panel, purged and reinstalled it, reinstalled gnome, resetted the panel, deleted all gnome-config folders in my home directory, checked all (?) applet autostart locations and exchanged the libclock-applet.so with a copy from my Jaunty live-cd.
Nothing worked, so that I guess it's not the file that's broken, but the way it is processed by gnome or gtk or something.
Does anyone know how to fix this or at least how I prevent the applet getting started by the panel?

Happy Mother's Day everyone.

---

### Post by fraktalek on 2009-05-24
How did you solve it?

I've just booted to 9.04 LiveCD and panel keeps crashing there too... so I guess I'll rather postpone the upgrade to 9.04 I wanted to do today..

---

### Post by dacyai on 2010-02-01
This happened to me upon installing jaunty.  If anyone knows how to fix it, please tell me.

---

### Post by WSmart on 2011-01-08
I get this quite often.  You can end the gnome-panel process and the panel will probably load properly right after that.  I think a delay on the gnome-panel at startup would make it more stable.  It's just when the system is booting and there's heavy system load, that seems to be the problem.   Probably depends on what applets you have on the panel(s) too.  I don't know how to set a delay on it.  I don't see gnome-panel as part of the startup applications.  

Thanks all. 

Be real, be sober.

---

