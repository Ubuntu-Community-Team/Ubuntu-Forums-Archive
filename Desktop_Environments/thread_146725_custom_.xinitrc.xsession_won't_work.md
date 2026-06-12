---
title: "custom .xinitrc/.xsession won't work"
date: 2006-03-18
forum: Desktop Environments
---

### Post by dbunder on 2006-03-18
I followed the instructions, word by word, in [https://wiki.ubuntu.com/CustomXSession?highlight=%28xsession%29](https://wiki.ubuntu.com/CustomXSession?highlight=%28xsession%29) to make myself a custom .xinitrc/.xsession.

Two problems:

1) When I go to kill gdm with "sudo /etc/init.d/gdm stop" it does it successfully.  When I log into a CLI with my user, "startx" won't start xwindows.  I can't paste exactly what it shuts down as, cause I'm on another PC.  From what I can see, it starts to read my xorg.conf, complains about some GL modules not having symbols (harmless, probably), then libfb.a:fbmmx.o: no symbols found.  It then loads the Synaptics driver (using a laptop/touchpad) with no errors, says a bunch of font renderers are already registered.  Then "waiting for X server to shut down Synaptics DeviceOff called" and back to command prompt.  This isn't a HUGE issue, since I won't be running startx ever, but where could it have gone wrong?  I checked for any other X sessions running, but none are.

2) In the Wiki entry it says to use the default session if you want to use your own .xinitrc/.xsession files from your home directory.  This is gonna be a pain to type out, but I start GDM, choose "Default System Session" from Sessions, type in my username/password, and X starts to load then bombs with a window that says:

```

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in again with one of the failsafe sessions to see if you can fix this problem.
```

There's a checkbox to show exactly what happened, and when I tick that, it says:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /etc/bin/X11/sessreg -a -w /var/log/wtmp -x "/var/lib/gdm/:0:.Xservers" -h "" -l ":0" "myusername"
/etc/gdm/Xsession: Beginning session setup...

```

That's it. I hit the OK button, and it sends me back to the gdm login.

My .xinitrc (linked to .xsession and flagged as +x):

```

#!/usr/bin/env bash
exec /usr/bin/syndaemon -d -i1
exec /usr/bin/gnome-terminal&

```

Am I expected to start up a gnome session in my .xinitrc, or should that be covered by the default setup?  At the bottom of that wiki page, I don't see any calls to gnome-session in the author's .xinitrc.  A bit confused here.

Thanks so much for any help to my (obviously) n00b question. ;)

---

### Post by 5-HT on 2006-03-18
I think there may be two things going on here.

One may be a problem pertaining to syndaemon (1), the other with your .xinitrc script (2).

(1)
From reading the man page for syndaemon, I'm greeted with this:
```
 This program needs SHMConfig "on" in your XFree86 Synaptics Touchpad configuration. 
``` 
Have you been able to run syndaemon before? 
If not, looks like you may need that flag set to avoid the issue you were describing.
It could be something else entirely, but that may be a good place to start.
Also, you could be getting those errors because there was a problem with your .xinitrc.

(2)
In terms of the .xinitrc script...
[quote=dbunder] Am I expected to start up a gnome session in my .xinitrc, or should that be covered by the default setup?  [/quote] 
Yes, you do need to include the command to start a gnome session (gnome-session).

Here is one that should work that leaves out syndaemon:

```

[FONT=monospace]#!/usr/bin/env bash
/usr/bin/gnome-terminal &
exec gnome-session [/FONT]
```[FONT=monospace]


Here is one that may work that includes syndaemon (if changing the relevant entry in xorg.conf fixes the problem, or if there isn't a prob with the syndaemon config in the first place):

[/FONT]```
[FONT=monospace]#!/usr/bin/env bash
/usr/bin/syndaemon -d -il
/usr/bin/gnome-terminal &
exec gnome-session [/FONT]
```[FONT=monospace]

As before, you'll need to make a symbolic link from ~/.xinitrc to ~/.xsession if you'd like to use GDM.

Hope this will be of some help.
[/FONT]
[FONT=monospace]

[/FONT]

---

### Post by dbunder on 2006-03-19
Thanks much.  I thought that a session would be set up by default, but I guess not. :)  And SHMConfig is on.  So that wasn't an issue.  I'll have it all set up nice after dinner.

---

