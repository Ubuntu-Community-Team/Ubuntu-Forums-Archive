---
title: "Navigating the Desktop Options"
date: 2017-01-12
forum: Desktop Environments
---

### Post by noleks on 2017-01-12
Hi:
I just upgraded from Ubuntu 14.04 to 16.04 the other day, and it was a little easier than I expected.
However, the desktop has changed in a good way, there are a few things I'd change if I could, but it really raises a fundamental question I can't answer:

What desktop system am I using? :confused:

I have a snapshot of my desktop below.  The launcher that used to be on the left side is gone, and replaced with an application menu on the top bar and the ability to drag & drop my most-used launchers to the bottom bar.  That is a good thing, IMO.

I think that it would answer MANY questions if someone could put together a wiki which could:

a) Give a step-by-step formula to identify a user's current desktop system (and perhaps likely plugins which make sense to mix and match?)
b) Establish standard terminology for the major objects used in the various desktop systems
c) Provide the most-requested tweaks for each system, and which tools should be used for each (ccsm for example is new this time around, I think)
d) List system mix & match packages/features that should NOT be used (and why?)

It seems like there is the possibility to mix & match several systems, for instance when I activated the Unity plugin in ccsm, it reported several conflicts with other already-active systems.  I had no idea which system should win, for each conflicting setting that it presented.

For me specifically, I'd like the launchers on the bottom bar (picture included below, what is that bar even called?  The Task Bar?) to live left of the active window buttons, so they don't get shifted right every time I launch a new window on the desktop.  I'd also like to add the Ubuntu Search functionality to the top bar, whatever it's called... "Menu Bar"?

Overall I'm happy with where I'm heading, I could just use a little more help knowing how I got here and how to get to my desired destination.

[ATTACH=CONFIG]273149[/ATTACH]

---

### Post by howefield on 2017-01-12
> **noleks said:**
> What desktop system am I using?

What desktop environment were you running before the upgrade ?

Does the output of 

```
echo $DESKTOP_SESSION
```

give you anything worthwhile ?

---

### Post by Frogs Hair on 2017-01-12
It appears to be gnome-session-flashback and the command could confirm this. This is not the default session in Ubuntu .

---

### Post by noleks on 2017-01-12
UBUNTU:~> echo $DESKTOP_SESSION 
gnome-flashback-compiz

That's okay though I think I like it, I just need a few helpful hints I guess.
I just tried adding launchers to the top bar and I can't get rid of them.  Whoops!

---

### Post by Frogs Hair on 2017-01-12
Try Ctrl+Alt+right click or super key/windows key + Alt +right click to change panel options.

---

### Post by noleks on 2017-01-13
Yes, that worked!  Thanks so much!
I think I'm pretty happy with my particular environment, now, though the Ubuntu search was nice and I don't see how to get it back.
Is there a wiki topic out there for setting up your desktop that begins with "echo $DESKTOP_SESSION"?
I really think it would reduce the number of posts if something existed.

---

### Post by Frogs Hair on 2017-01-13
You can select installed desktop environments during login from the icon on the top right side of the greeter box where the password is entered.

---

