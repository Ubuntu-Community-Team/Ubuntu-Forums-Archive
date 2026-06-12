---
title: "Lost Volume Applet"
date: 2010-06-26
forum: Desktop Environments
---

### Post by rfbeck on 2010-06-26
I use Lucid with Gnome. I lost the volume applet on the top panel. I tried to search for it under "Add to panel...", but couldn't find it. Can anyone help?

Thanks,
______
Robert

---

### Post by moongia on 2010-06-27
its called "indicator applet",,hope that helps..

---

### Post by Dr_Willis on 2010-06-27
The Volume Applet is actually part of the Applet that also gives you the mail icon. People often dont want the mail icon, remove it then find both missing. :)

If you dont want both icons. You Could just run the 
 **gnome-volume-control-applet** and set it to startup automatically  with the startup applications tool.


If you want to remove the mail icon for all users, in all situations I have heard removing the following will do the trick.

[HTML]sudo apt-get remove indicator-messages indicator-me[/HTML]

With the above you would just have the Speaker icon. (after you get them both back of course)


If you want them both back, well i cant figure out which panel applet it is either, i HATE how the panel applets are getting 'merged' into bigger 'combo' applets.  One of issues with how gnome and its panels work I guess.  

However. to **totally reset the gnome panels**  the following command will do that.

```
gconftool --recursive-unset /apps/panel && killall gnome-
panel
```

---

### Post by rfbeck on 2010-06-27
Thanks guys. I got it back now. Nice!
______
Robert

---

