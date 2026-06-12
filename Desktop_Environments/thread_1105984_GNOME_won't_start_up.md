---
title: "GNOME won't start up"
date: 2009-03-25
forum: Desktop Environments
---

### Post by kshsj777 on 2009-03-25
When I login into the GNOME session, the background briefly appears, then a a purplish blue background, then black and then back to the login screen.

Logging into Xfce session works.  I tried reinstalling the gnome desktop, reinstalling x.org and similar files to it, reinstalling xrandr etc.

I was following this tutorial: [http://forum.eeeuser.com/viewtopic.php?id=38348](http://forum.eeeuser.com/viewtopic.php?id=38348) because previously when I did part of the tutorial, the resolution on my external monitor was too low.  Now it wasn't getting a signal at all, so I went back to do it again.

I have a wind but I though it'd work here too.

Everything was fine until I did this:     xrandr --output VGA --mode 1680x1050  (I didn't do it last time though)

That made the resolution on my wind change so I rebooted my computer to make it go back to normal and voila now GNOME won't start up.

Any idea how to fix it?
Thanks
777

---

### Post by mhgsys on 2009-03-25
could you post your

/etc/X11/xorg.conf

edit: I saw the link you followed. 
In case you made the backup... to this.. in case you didn't then DON'T

```

sudo nano /etc/X11/xorg.conf.orig

```

Then hit ctrl + O to write it , and name it /etc/X11/xorg.conf
enter
hit Ctrl + X to exit. 

then:
```

sudo /etc/init.d/gdm restart

```

Edit: If that didn't work then 
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by kshsj777 on 2009-03-25
Thanks.  I think I already restored the configuration file because when I last looked it, it was set to the way it was before I made changes to it.

sudo dpkg-reconfigure xserver-xorg

I tried this, and it didn't fix it.  I'm starting to think I need to reinstall Ubuntu.

---

### Post by mhgsys on 2009-03-25
have you tried 

```

xrandr --output VGA --mode 1280x1024

```

or 
```

xrandr --output VGA --mode  1024x768

```


have a look here as well, maybe the info davidshere provided can help you
[http://ubuntuforums.org/showthread.php?t=1093433](http://ubuntuforums.org/showthread.php?t=1093433)

---

### Post by kshsj777 on 2009-03-25
I tried that using 1024 by 600 and it said it couldn't find it that resolution, so I gave up.  However, a few hours later, I tried going into GNOME again and it worked.  I don't why, but I'm just so happy that it is working again!!!

---

### Post by mhgsys on 2009-03-26
You can either use 800X600 or 1024x768, not 1024x600.

I guess it's working now because the resolution will be set 1024x768
Can you check that in 
>System>Preferences>Screen resololution.?

Anyway, I'm pretty sure 1024x600 is not a resolution which will work.
You'd better change it to 1024x768 in xorg.conf and typ ```


xrandr --output VGA --mode  1024x768

``` 
in a terminal again.

I guess X will automatically try resolutions, but this takes time as you seen before.
> 
However, a few hours later, I tried going into GNOME again and it worked. I don't why, but I'm just so happy that it is working again!!!


---

