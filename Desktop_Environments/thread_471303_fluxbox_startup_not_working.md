---
title: "fluxbox: startup not working"
date: 2007-06-11
forum: Desktop Environments
---

### Post by oldcpu on 2007-06-11
My ~/.fluxbox/startup as follows:
```
#!/bin/bash
conky &
firefox &
exit 0
```
Neither would start up.  startup is executable.

---

### Post by RedSquirrel on 2007-06-11
It's not a bash script, so you don't need the first and last lines you have there.

Make it  like this:

```
conky &
firefox &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox

```Are you using gdm? Your /usr/share/xessions/fluxbox.desktop file should look like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

```starfluxbox is a script that will load the ~/.fluxbox/startup file for you. (If you rename the startup file, then log out and log back in again, startfluxbox will create the default startup file for you.)

---

### Post by oldcpu on 2007-06-11
I now have
```
conky &
firefox &

exec /usr/bin/fluxbox
```
but it still would not startup.

> Are you using gdm?
I am not sure what that is.  I installed Fiesty server, and manually installed the rest of the stuff.

> Your /usr/share/xessions/fluxbox.desktop file should look like this:
Yes, it does have this line:```

Exec=/usr/bin/startfluxbox
```

As mentioned above, I installed Feisty server and other stuff manually.  So I start X, by using `startx` after logging in.  Would this change how startup in ~/.fluxbox behaves?

---

### Post by RedSquirrel on 2007-06-12
> **oldcpu said:**
> I am not sure what that is.  I installed Fiesty server, and manually installed the rest of the stuff.

gdm is the GNOME display manager.

[http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)

It seems you are not using it, and that's just fine.


> **oldcpu said:**
>  Yes, it does have this line:```

Exec=/usr/bin/startfluxbox
```As mentioned above, I installed Feisty server and other stuff manually.  So I start X, by using `startx` after logging in.  Would this change how startup in ~/.fluxbox behaves?

The important point is that you must call startfluxbox. 

If you use ~/.xinitrc, put 'exec startfluxbox' as the last line in that file.

I will mentioned here that there is excellent documentation in the man pages:

```
man fluxbox
man startfluxbox
man fluxstyle

```

The rest of this discussion has moved to this thread:

[http://ubuntuforums.org/showthread.php?t=471229](http://ubuntuforums.org/showthread.php?t=471229)

---

