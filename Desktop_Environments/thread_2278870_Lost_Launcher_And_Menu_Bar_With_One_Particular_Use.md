---
title: "Lost Launcher And Menu Bar With One Particular User ID (15.04 32 bit)"
date: 2015-05-19
forum: Desktop Environments
---

### Post by n4lbl on 2015-05-19
I've been running 15.04 for a few weeks satisfactorily.  After restarting from Win7 (no, I don't believe that that is the cause) on my "usual" user ID I lost both the Launcher and the menu bar.  All the other IDs and guest work fine.

On the non-working ID the only thing I can figure out to do us right-click on the desktop and select change-desktop-background to get to system settings.  I can't find anything there to fix it and I can't get rid system settings without the menu bar.  Yes, I have tried appearance/behavior there.  All I know to do is Cntl-Alt-F7 to get to another ID.

I have tried logging in to the non-working ID with Gnome instead of Ubuntu(default) which I think is also called Unity.  No help.  I ordinarily use Ubuntu(default).

Thanks for any help.

Other data (just in case):
Laptop is ASUS Eee PC 1015 PEM w/ 2 GB memory
15.04, 32 bit version
Since the problem started I did run the Software Updater

---

### Post by dino99 on 2015-05-20
maybe you have set (or that user id) the setting to autohide

---

### Post by grahammechanical on 2015-05-20
In the user session with just the background wallpaper it should be possible to open a terminal from that menu that comes up when we right click the wallpaper. Try running 

```
setsid unity
```

another one to try is

```
dconf reset -f /org/compiz/
```

Regards.

---

### Post by n4lbl on 2015-05-20
Edit:  I forgot to use quote.  This is a reply to dino99 suggesting "  maybe you have set (or that user id) the setting to autohide  ".  End edit.

Thanks, but that doesn't work.  Turning auto-hide off should pin the launcher in place and that doesn't work.  Adjusting the auto-hide sensitivity doesn't help either.

Thanks again.

---

### Post by n4lbl on 2015-05-20
> **grahammechanical said:**
> In the user session with just the background wallpaper it should be possible to open a terminal from that menu that comes up when we right click the wallpaper. Try running 

```
setsid unity
```

another one to try is

```
dconf reset -f /org/compiz/
```

Regards.

Thanks..  I obviously couldn't open a terminal session with the launcher.  Poking around I learned that cntl+alt+t should work but it didn't work in the problem user ID.  I does work in the user ID I am currently using on the same machine.  

Cntl+alt+F7 can get me from the problem user ID to this good one.  Funny, but that isn't reversible.

Thanks again.

---

### Post by n4lbl on 2015-05-20
> **grahammechanical said:**
> In the user session with just the background wallpaper it should be possible to open a terminal from that menu that comes up when we right click the wallpaper. Try running 

```
setsid unity
```

another one to try is

```
dconf reset -f /org/compiz/
```

Regards.

Grahammechanical:   Knucklehead that I am, I didn't realize that right-clicking on the desktop provided an invitation to a terminal session.  Thats the good news.  The bad news is no progress.  The setsid command re-started the session, just as it was before.  The dconf made no difference that I can tell.

Thanks,,, and you did get me to recognize that I can issue terminal commands.

---

### Post by n4lbl on 2015-05-20
Seems solved (for the moment)!!  I don't really know why but I'll state what I did.

I have re-booted many times.  Just before the "cure" I ran the Software Updater which only had one change and it was to the OS.  Upon completion re-booting was not called for.  

I spent some time puzzling over the system log.  I decided to re-boot, sign in to a good user ID and do nothing there, and sign into the failing user ID and also do nothing.  My goal was to read the system log with the minimum extraneous stuff to confuse me.  What actually happened was that the problem user ID was back to normal.  All was OK.  The launcher and the menu bar were back.  The only symptom I found was that the launcher icon size was set to the default 42 units.  Maybe that is a sign!  Maybe not.

I'll mark this closed (solved?) when I've lived with it for a while.  Did the maintenance fix it?  Actually I guess so.  I don't know how to look up exactly what the last maintenance was though.

Thanks to all.

---

### Post by n4lbl on 2015-05-22
Well, I'll call this solved, even if I don't know what happened.  I don't know why only one user was affected.  I don't really know if the maintenance helped but I believe it did.  I don't even know what the maintenance was.

Thank you everyone for trying to help.

---

### Post by kdwarn on 2015-08-05
> **grahammechanical said:**
> In the user session with just the background wallpaper it should be possible to open a terminal from that menu that comes up when we right click the wallpaper. Try running 

```
setsid unity
```

another one to try is

```
dconf reset -f /org/compiz/
```

Regards.

I was having the exact same problem, and the second bit worked. Thanks so much!

---

### Post by gavsue on 2015-11-20
> **grahammechanical said:**
> In the user session with just the background wallpaper it should be possible to open a terminal from that menu that comes up when we right click the wallpaper. Try running 

```
setsid unity
```

another one to try is

```
dconf reset -f /org/compiz/
```

Regards.

This worked for me. Right click desktop > open terminal > enter the commands > restarted computer> :)

---

