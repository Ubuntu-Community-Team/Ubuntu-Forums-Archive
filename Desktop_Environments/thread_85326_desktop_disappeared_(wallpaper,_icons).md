---
title: "desktop disappeared (wallpaper, icons)"
date: 2005-11-02
forum: Desktop Environments
---

### Post by mgor on 2005-11-02
okey, i sat yesterday and played around in the gconf editor.
but as far i can remember i didn't change anything vital, only a key that
specified which browser to use (/desktop/gnome/applications/browser/exec), it said 'epiphany' (hope i got the name right ;) ) and i changed it to 'firefox'.

anyway, when i started my laptop this morning the desktop was gone, no wallpaper and no icons, there's no menu when right clicking.

so i thought i must've changed something in the gconf editor, so i moved everything that could contain any gnome settings (~/.gconf, ~/.gnome2 ... )
but the desktop still is gone.

does anyone know how to get it back? ;)

btw,
/desktop/gnome/background/draw_background is set
hm, and i remembered i saw an key about "show icons on desktop", but i couldn't find it now :???:

---

### Post by tmadsen on 2005-11-02
looked around in applications->system tools->configuration editor->desktop?

---

### Post by rjwood on 2005-11-02
/desktop/gnome/applications/browser/exec' and i changed it to 'firefox'.

what did it say before you changed it to firefox??

---

### Post by mgor on 2005-11-02
[QUOTE=rjwood]/desktop/gnome/applications/browser/exec' and i changed it to 'firefox'.

what did it say before you changed it to firefox??[/QUOTE]

ops, paste missmatch :-)
it said epiphany, after i moved all the "settings" folders it changed back to epiphany and still didn't work.

---

### Post by rjwood on 2005-11-02
if you have a command line try sudo startx

---

### Post by mgor on 2005-11-02
[QUOTE=rjwood]if you have a command line try sudo startx[/QUOTE]

the graphical interface is working. gnome-panel etc. it's only the desktop; wallpaper and icons that's not working.

---

### Post by mgor on 2005-11-02
[QUOTE=tmadsen]looked around in applications->system tools->configuration editor->desktop?[/QUOTE]

yepp, i've looked at most of the options available.

---

### Post by rjwood on 2005-11-02
did you try system>preferences>filemanager for icons and backgrounds for wallpaper?

---

### Post by mgor on 2005-11-02
it's just like the program that should "take care of" the desktop, like gnome-panel for the panels isn't running.

there's NO menu when right clicking the desktop area.

---

### Post by tmadsen on 2005-11-02
Hmm ... tried: Applications -> System Tools -> Configuration Editor -> apps-> nautilus -> preferences -> check show desktop?

else there's this /usr/share/gnome/default.session, if you're saying that it might be the panel, that's fucked. Mine looks like this:

> # This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=8
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
4,id=default4
4,Priority=40
4,RestartCommand=gnome-volume-manager --sm-client-id default4
5,id=default5
5,Priority=40
5,RestartCommand=magicdev --sm-client-id default5
6,id=default6
6,Priority=50
6,RestartCommand=vino-session --sm-client-id default6
7,id=default7
7,Priority=50
7,RestartCommand=update-notifier --sm-client-id default7


---

### Post by mgor on 2005-11-02
/apps/nautilus/preferences/show_desktop is checked and my /usr/share/gnome/default.session is identical to yours :(

---

### Post by Fmac on 2005-11-02
Have you tried 'killall nautilus'?

Usually works for me when I get that.

---

### Post by mgor on 2005-11-03
it's working now, seemed like nautilus wasen't working correctly. not even after a reboot and the gnome splash said 'starting nautilus'.

---

### Post by Absorbed on 2007-10-19
I've just had exactly the same problem in Gutsy. I used gconf-editor to remove icons for mounted volumes. The icon didn't disappear immediately, as it has done before, and when I next logged in there was no wallpaper or icons.

It's fixed now, by doing the following:

```
sudo killall nautilus
sudo nautilus &
```

Now when I use gconf-editor to change what icons appear on the desktop, they appear and disappear immediately.

---

### Post by Foxmike on 2007-10-20
I have the exact same behaviour in Gusty, I'm planning to fill a bug about that.  It seems that a zombie instance of nautilus (talking as much CPU as it can) il lying around in the background.  It happens to begin at the second login after the machine is rebooted.  If anyone can get a trace (I'll only have time late tonight), please post it here or file a bug in launchpad (or I'll do it tonight...;))

If anyone has some more detail concerning this behaviour, it'll surely help make the bug report better...

---

### Post by pisica on 2007-10-24
Right. I have the same problem (under Gutsy Gibbon, freshly installed) (though never touched the gconf editor!).
Namely, when the computer starts for the first time, everything is ok. But, if I log out and re-log in, then there are no icons on the desktop, etc. and (since I have a dual core Intel) 98% of one of the CPU's is used, and 60% of the other CPU too.
The "solution" is to execute in terminal a "killall -9 nautilus", and then everything becomes normal. So, I made a script, called clean.sh :

[COLOR="Blue"]#!/bin/bash

killall -9 nautilus 1>/dev/null
nautilus&

exit
[/COLOR]
and added it to the System > Preferences > Sessions, to be taken into account when the new session starts.

Unfortunately, it has no effect !!!

PS Re-installing nautilus is useless.

Someone has an ideea? Is it a real bug ? (or I'm just stupid?)

---

### Post by pisica on 2007-10-25
> **Foxmike said:**
> I have the exact same behaviour in Gusty, I'm planning to fill a bug about that.  It seems that a zombie instance of nautilus (talking as much CPU as it can) il lying around in the background.  It happens to begin at the second login after the machine is rebooted.  If anyone can get a trace (I'll only have time late tonight), please post it here or file a bug in launchpad (or I'll do it tonight...;))

If anyone has some more detail concerning this behaviour, it'll surely help make the bug report better...

It seems it has been already reported as a bug: see

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471)

and the duplicate bugs from there.

What bothers me is that they classified it as being of "medium" importance.

---

### Post by markonhismobile on 2007-10-28
Ive just had this problem, it occured after I was playing around with Startupmanager so I assumed it was something to do with that. I couldn't understand why as that only should effect my menu.lst file!

After reading this I tried the method of killing nautilus but it reported it wasn't running so I ran nautilus from a terminal and I got my icons back. I checked the option in the System-Preferences-Sessions to remember applications running and rebooted and I had my icons and wallpaper back!

Not sure if this will help anyone else but I thought I'd share it!

---

### Post by sboysel on 2007-11-04
I have the same problem in Gutsy but it happened after i switched from nautilus to thunar (be redirecting all commands for nautilus to thunar).  But now my desktop is black, i cannot right click, and there are no icons.  I can make the wallpaper show up by setting it in appearance.
Please Help!

---

