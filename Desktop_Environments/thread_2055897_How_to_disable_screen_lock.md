---
title: "How to disable screen lock?"
date: 2012-09-10
forum: Desktop Environments
---

### Post by arcull on 2012-09-10
Hi there,

First I did install lubuntu version 12.04 64bit. After a while I decided to try some other desktops, so I installed via synaptic also xfce and gnome 3. So now I am currently using gnome, and much or less everything ok. But I can't figure out how to disable screen lock which turns on whenever I leave the PC for cca. 10 mins. I did check the settings in screen saver panel, but the tick "Lock screen after..." is not activated. I check also in gconf-editor under /desktop/gnome/lockdown/disable_lock_screen is ticked. But the screen does lock despite these settings.,....grrrr. Any ideas maybe, how can I solve this issue? Tanks for your help.

---

### Post by december0123 on 2012-09-10
Do you have any of these processes active? 
[B]gnome-screensaver
[/B]
[B]xscreensaver

[/B]If so, try killing them.

---

### Post by arcull on 2012-09-10
>               **Re: How to disable screen lock?**
         Do you have any of these processes active? 
[B]gnome-screensaver
[/B]
[B]xscreensaver

[/B]If so, try killing them.      yup, that's it, there is a process gnome-screensaver running, if I kill it, then the screen does not lock anymore. Any idea how do I prevent this process from starting, because killing it doesn't sound to handy?

---

### Post by december0123 on 2012-09-10
I don't use gnome, so I don't really know how to do it, but google search does give some results like **[this]("http://www.ehow.com/how_6900114_disable-gnome-screensaver.html")**, so you should be able to find the solution. Good luck!

---

### Post by rybnik on 2012-09-10
If you're using Gnome 2 or Gnome Classic Fallback, then this will work:

1. Right-click the top panel.
2. Add to panel.
3. Inhibit Applet.
4. Click the inhibit applet icon so the red circle slash appears through it.

If you're using a different Gnome or Unity, I think you should be able to set up the gnome fallback, do the above in it, and then go back to whatever you're using and the settings should transfer over.

Let me know if that works...

---

### Post by arcull on 2012-09-10
> I don't use gnome, so I don't really know how to do it, but google search does give some results like **[this]("http://www.ehow.com/how_6900114_disable-gnome-screensaver.html")**, so you should be able to find the solution. Good luck! 	 thanks buddy

---

### Post by arcull on 2012-09-10
> If you're using Gnome 2 or Gnome Classic Fallback, then this will work:

1. Right-click the top panel.
2. Add to panel.
3. Inhibit Applet.
4. Click the inhibit applet icon so the red circle slash appears through it.

If you're using a different Gnome or Unity, I think you should be able  to set up the gnome fallback, do the above in it, and then go back to  whatever you're using and the settings should transfer over.

Let me know if that works... the solution from december0123 looks like working, so for now I'll leave it like this, I appreciate your help anyway, thanks. Maybe this can help someone else too :)

---

