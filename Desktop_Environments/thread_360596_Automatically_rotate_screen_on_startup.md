---
title: "Automatically rotate screen on startup"
date: 2007-02-13
forum: Desktop Environments
---

### Post by MikeDX on 2007-02-13
Apologies if this is in the wrong section

Dear all

I have now got two very successful ubuntu installs (6.10) and all is going well. XP has been wiped off completely

I've set up the nvidia drivers and beryl/emerald on the desktop pc but i need the screen to be rotated 180degrees as soon as the x login screen appears. If i hardcode into xorg.conf "rotation" = "inverted" then I dont get beryl on startup and the whole desktop is a lot slower, however if i start the session and go to screen resolution and choose inverted, then i get the lovely beryl desktop and inverted screen

i need the screen inverted as my monitor is mounted from above, so on bootup my whole screen is upside down.. there is no way around this as i can't afford the wires to be all trailing.

choosing the desktop to be the default setting of inverted does nothing!

very frustrating.. is there an xorg.conf setting or something that will allow me to keep my screen rotated 180 degrees and keep an accelerated desktop?

I'm competent.. so don't worry about scaring me with terminology! I've looked all the usual places but found nothing so far :(

Thanks in advance!:KS

---

### Post by MikeDX on 2007-02-14
Hmm.. seems nobody could help

I've got a workaround for this now but i don't like it.

I automatically have my default user login and in the session scripts i have entered 

```

xrandr -o inverted
```

so now when the computer starts up, once gnome is up and running, beryl starts and the screen is rotated..

not a great fix. Is there an auto-run feature for the graphical login that I could enter the same options?

---

### Post by v8YKxgHe on 2007-02-28
You could add the command to your startup session?

System->Prefs->Session->Startup Tab.

Regards,
Alex

---

### Post by RichardBronosky on 2007-03-22
The solution that MikeDX, and I, need is to run a script after X starts, but before the login.  I would be satisfied to have my script run while the login screen is showing, as long as xrandr can do its magic and cause the login screen to get rotated.  The Session Startup stuff doesn't happen until after the user logs in.  Which means my Windows using officemates see that I have to use a [sideways in my case] login screen.

Please advise.

---

### Post by john3333 on 2007-06-10
I'm pretty new to Linux (and Feisty), but before I got my 90-degree screen rotation to work by inserting the "RandRRotation"  option into the xorg.conf I think I was using a command in xorg.conf which automatically started it in the portrait (90-degree left) mode.
That command, in the Device section of xorg.conf, was
Option     "Rotate"    "CCW"
So I assume if you were to type in the instruction for 'inverted' where I typed in "CCW" (for counter clockwise) then your screen would start in the 'inverted' position.
Therefore, I assume that if you:
1. Delete the line in xorg.conf which says Option   RandRRotation  On, and then:
2. Type in:  Option    "Rotate"    "Inverted"
then your screen would start in the inverted mode.
Perhaps someone else can clarify this. 
And, before doing this, of course, back up your xorg.conf file so you can restore it if my suggestion screws things up.

---

