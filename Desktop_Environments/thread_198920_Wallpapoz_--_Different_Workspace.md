---
title: "Wallpapoz -- Different Workspace?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by ~LoKe on 2006-06-17
I've got Wallpapoz installed and it's up and running.  The only problem is...I can't seem to find out how to add wallpapers for the other workspaces.  As is, I can only add wallpapers to workspace 1.  Could anyone please explain to me how I would go about doing this for the other workspaces?

Thanks!

---

### Post by steveneddy on 2006-06-18
OK - Go to Applications-->Accessories-->Wallpapoz  

- on the left of the open window you will see the four desktops. 

The little arrows next to the 1,2,3 & 4...click the little arrow. A list will drop down with the path to the wallpaper you are using.  

Right click the path and a menu appears that gives you the option on choosing another wallpaper.

Should be pretty much self explanitory after that.

-SE

You have to have wallpapoz in the startup programs for it to run at start up, you know. I believe that if you start the daemon from the Wallpapoz set up screen, and then log out, your session will be saved. 

Now go get some pretty wallpapers.

---

### Post by ~LoKe on 2006-06-18
Unfortunately it's not so simple in my case.  I have only one workspace arrow available to me.  I use XGL, could this possibly be the cause?

Thanks!

[IMG]http://images.x04d.com/wallpapoz.png[/IMG]

---

### Post by steveneddy on 2006-06-18
Hmmm...I understand - I stopped using XGL after many things I liked and used were unavailable after switching to XGL. I don't have an answer for you on that one. 
*******************************
](*,) 
I've sat here this morning messing around with it, and short of installing XGL again, I believe that, given the details, that I don't know. I will come back to this on often though. I would like to know the answer to this one.

Sorry I couldn't help. -SE

---

### Post by ~LoKe on 2006-06-18
Thanks for at least trying. =]  Other than this, I've experienced no other major problems with the use of XGL (short of having to log on/off/back on/whatever in order to get it to run).  I'm obsessed with XGL now, heh.

---

### Post by RoNoVe on 2006-06-18
Having to log off/log back on probably has to do with the loading time of the xgl-xserver, which needs a little more time than a normal xorg to startup.. How to fix it depends on how you start xgl (xgl != compiz)

If you could tell me how you start it, I could probably help you, however I'm having some problems with GL atm.

---

### Post by ~LoKe on 2006-06-18
It's actually more complicated than I had previously mentioned.  The problem is...I tried many different methods to get this to work, and I'm not sure which one is doing what.  To start...When I first log in, it's not running.  I then restart (ctr alt backspace) and log in to the same account, but instead of hitting "return to previous login" I choose "log in anyways".  Then, it'll come up and I can see that it's working, but it'll magically bring me back to the login screen again.  Then I log in and choose "return to previous login" and all is good. Heh, weird.

Anyways, this is the script that starts XGL/Compiz/whatever.  It's a startup command for my session.

/usr/bin/thefuture 

```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

---

### Post by ~LoKe on 2006-06-18
Anyone? =]

---

### Post by RoNoVe on 2006-06-18
I assume you startup xgl itself (the xserver) from within gdm?

---

### Post by ~LoKe on 2006-06-18
I'm not entirely sure what you're asking.  I've got thefuture running on startup, other than that it does it on its own.

---

### Post by Lord Illidan on 2006-06-18
I believe XGL makes GNOME believe it only uses one workspace. In fact, the workspace switcher in the panel shows only 1 large elongated one, instead of 4 seperate ones.

---

### Post by Anduu on 2006-06-18
[QUOTE=Lord Illidan]I believe XGL makes GNOME believe it only uses one workspace. In fact, the workspace switcher in the panel shows only 1 large elongated one, instead of 4 seperate ones.[/QUOTE]

Yup with XGL running gnome is no longer in control of workspace switching.

---

### Post by ~LoKe on 2006-06-18
That actually makes a lot of sense.  Thanks. =]

Now, is there any way of me using a different wallpaper for each workspace that will work with XGL?

---

### Post by Anduu on 2006-06-18
AFAIK there isn't...yet ;)

---

