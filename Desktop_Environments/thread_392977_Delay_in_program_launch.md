---
title: "Delay in program launch"
date: 2007-03-25
forum: Desktop Environments
---

### Post by Mark Erbaugh on 2007-03-25
When I use the menus to launch a program or when I double click an icon to launch the associtated program, the program loads quickly, but there is another item that shows up in the bottom panel that Starting XXX (XXX is the program). While this item is displayed, the cursor is the wait (rotating circle) cursor, but I can still use the mouse. The Starting XXX item eventually goes away and the cursor returns to normal.

On the other hand, if I open a terminal window and launch the same program with a command, the program loads quickly and there is no delay with the wait cursor or the Starting XXX item in the bottom panel.

What is that Starting XXX thing doing?  Is there a way to disable it?

This is using gnome under Dapper.

Thanks,
Mark

---

### Post by mgmiller on 2007-03-25
The only place I noticed that was with Evolution.  It only happens sometimes.  I never did figure out why it does this because Evolution works fine even thought the hourglass is spinning.  I am running Edgy upgraded from Dapper upgraded from Breezy upgraded from Hoary.  I figure I must have some cobwebs in there somewhere, but it's been pretty smooth sailing for me.

---

### Post by SuSUntu on 2007-03-25
I only get the described behavior when launching root applications such as Synaptic, root Nautilus Browser, etc. The behavior is still evident whether these apps are launched from an icon or the terminal **as long as I use 'gksudo' to launch them**.

Perhaps you are only getting the panel "Starting' icon when using the icon launchers because the underlying code is 'gksudo' and when you launch them from a terminal you are using 'sudo'. Using 'sudo' does not cause the "Starting...' icon to appear for me, nor does the mouse animation appear.

Try these tests:

- Launch 'gedit' with:

```

sudo gedit

```

Here, I get a quick launch without the 'Starting  Administrative Application' icon and no prolonged mouse animation.

- Launch 'gedit' with:

```

gksudo gedit

```

Here, I get a quick launch with the 'Starting  Administrative Application' icon and prolonged mouse animation.

Also, watch the differences between the two methods using your System Monitor application.

Why 'gksudo' has this behavior (i.e, not removing its residual icon and mouse animation after the main app has successfully started), I do not know. However, I have experienced this in both Dapper and Edgy, and maybe even Breezy (I can't recall). It seems like a bug that could easily be rectified.

If this is occurring even for regular (non-root) apps, I cannot comment because this does not occur on my installations. It probably would with heavy,  resource-intensive apps like Evolution if I was running a slower PC.

---

### Post by Mark Erbaugh on 2007-03-25
> **SuSUntu said:**
> 
If this is occurring even for regular (non-root) apps, I cannot comment because this does not occur on my installations. It probably would with heavy,  resource-intensive apps like Evolution if I was running a slower PC.

I notice this with non-root applications, such a the Python IDE, Idle and also the games installed by default.

---

