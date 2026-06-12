---
title: "n00b stuck on openbox, no desktop"
date: 2011-11-13
forum: Desktop Environments
---

### Post by resero on 2011-11-13
Hi, I'm running Ubuntu 11.10, and never changed the default login (no pass required).
I've installed the lxde packages to test it.
What I did to change the desktop was to logout and then choose a desktop on the login screen.
I tested lxde and back to unity, everything went fine.
So I noted two more desktops: Openbox and Gnome/Openbox. and logged on one of those (can't tell you what of those). This one has no menus and applications bars, just the windows managers. I can shutdown, but no logout, when I restart the SO logsin to this desktop, not the default.
I managed to run lxsession but I can't find a preference for the login screen (ask for password), nor user, and the logout button doesn't work.
Is there some terminal command line to logout, configure users or set the default desktop to unity?
Maybe a key combinartion to press during boot to force the login screen to appear?
Yes, I know this is such a lame question, but I'm stuck here and I couldn't find anything here or in the help.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Can you enter a command with Alt+F2?

If so, you could open an lx panel w/ Alt+F2 and
```

lxpanel

```

---

### Post by resero on 2011-11-13
mhh, a terminal you mean?
I already opened one with alt+ctrl+t 
and I'm running lxsession, but the logout button doesn't work.
[I]javier@javier-lp:~$ lxpanel
There is already an instance of LXPanel.  Now to exit
javier@javier-lp:~$[/I]
I don't want to run lxde, I just want to get to the login screen and choose unity and change my preference.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Ok, I see...
```
unity --replace
```
should get you your unity desktop back... then fix it from there!

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
You can also manually edit the config for lightDM (if you are using 11.10... otherwise it is GDM)  so if unity --replace doesn't work out, then
use 
```

update-alternatives --config x-session-manager 

```

---

### Post by haresear on 2011-11-13
> **resero said:**
> 
So I noted two more desktops: Openbox and Gnome/Openbox. and logged on one of those (can't tell you what of those). This one has no menus and applications bars, just the windows managers. I can shutdown, but no logout, when I restart the SO logsin to this desktop, not the default.


This may not help with your current situation, but in the Openbox session the desktop is just a blank monotone wallpaper -- no panel, no icons, no menu button. The default menu is displayed by a mouse right-click on the desktop. The menu is very sparse with only a few entries, and at the bottom is 'exit', which logs you out of the session and returns to the login screen.

---

### Post by resero on 2011-11-13
> **TREESofRIGHTEOUSNESS said:**
> Ok, I see...
```
unity --replace
```
should get you your unity desktop back... then fix it from there!

Yeah! this do it. Thanks:D

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
No problem!!  Glad I could help!

---

