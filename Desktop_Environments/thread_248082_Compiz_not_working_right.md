---
title: "Compiz not working right??"
date: 2006-08-31
forum: Desktop Environments
---

### Post by dyous87 on 2006-08-31
Hello,

I recently installed compiz and all the dependancies etc following directions that I found online however it doesn't work right at all and I don't know why. Everything seemed to be fine after the installation. I restarded my computer and my xserver didn't seem to be working correctly. The login screen never came up and instead a grey screen with a loading icon showerd. I hit ctrl, alt and backspace and it brang me to the comand line. So...i logged in and started x...it was a bit shakey but it finally started up. The only problem is that my computer doesn't appear to be using compiz because i still have my old window manager up. Even when trying to change themes with cgwd nothing happens...also my shutdown and restat button seem to have dissappered...any help would be greatly appreciated...

system specs:
intel core duo 1.6 gigs
2 gigs of ddr2 ram
ubuntu dapper drake
ati mobility radeon x1400

btw this is my /usr/bin/startcompiz.:
```
    #!/bin/sh

    # Start up Xgl, compiz, and GNOME


    # Run Xgl server on :1, on top of normal X

    # For an ATI Card:

    # Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &

    # For an Nvidia Card:

    # Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &


    # Tell subsequent X programs to access the Xgl server at :1

    DISPLAY=:1


    # For compiz-vanilla, g-w-d will be our window manager.

    # gnome-window-decorator &

    # For community compiz, cgwd will be our window manager.

    # cgwd &


    # Start Compiz

    compiz gconf &


    # Start GNOME

    exec gnome-session
```
thank you in advance,
dave

---

### Post by angkor on 2006-08-31
What howto are you following? 

Shouldn't you uncomment (remove the #) that ATI line and one of the decorators lines?

```
# Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &

# cgwd &
```

---

### Post by dyous87 on 2006-08-31
I was using the directions from this location: [http://www.chromakode.com/blog/2006/04/30/even-morebidly-lazy-compiz/](http://www.chromakode.com/blog/2006/04/30/even-morebidly-lazy-compiz/)
 
Also I uncommented what you told me to uncomment so now it looks like this:
```
     Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &

    # For an Nvidia Card:

    # Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &


    # Tell subsequent X programs to access the Xgl server at :1

    DISPLAY=:1


    # For compiz-vanilla, g-w-d will be our window manager.

    # gnome-window-decorator &

    # For community compiz, cgwd will be our window manager.

     cgwd &


    # Start Compiz

    compiz gconf &


    # Start GNOME

    exec gnome-session
```

I am restarting x right now to see if it works...

thanks
dave

edit: nope i just restarted x and it's still the same...i duno what's wrong with it hmmm...:confused:

---

### Post by dyous87 on 2006-08-31
now i completely restarted my computer and it appears i have no window manager at all...no windows...just screens that come up and cant me moved or minimized or anything...

---

### Post by angkor on 2006-08-31
> **dyous87 said:**
> now i completely restarted my computer and it appears i have no window manager at all...no windows...just screens that come up and cant me moved or minimized or anything...

what happens if you open a terminal and try to start the compiz script manually with 'startcompiz' (without the quotes)?

---

### Post by dyous87 on 2006-08-31
this is what happens:

```
david@david-laptop:~$ startcompiz

Fatal server error:
Server is already active for display 1
        If this server is no longer running, remove /tmp/.X1-lock
        and start again.

cgwd: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
gnome-session: you're already running a session manager
david@david-laptop:~$ compiz.real: Support for non power of two textures missingcompiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :1

```

---

### Post by angkor on 2006-08-31
did you try the --replace option? I think you can try this after entering startcompiz like you did before (when you don't have any window borders i mean)

```
cgwd --replace &
```

Also do a search on your error message on [http://www.compiz.net](http://www.compiz.net)

---

### Post by dyous87 on 2006-08-31
hmm no it didn't do anything...it just makes a bunch of gnome pannel applications quit unexpectedly...

---

