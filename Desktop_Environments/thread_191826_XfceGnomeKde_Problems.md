---
title: "Xfce/Gnome/Kde Problems"
date: 2006-06-08
forum: Desktop Environments
---

### Post by fazza on 2006-06-08
Hi people
I've just upgraded to 6.06, and everything seems fine, and some things (graphics) have got better. I thought I might give kubuntu and xubuntu a go, so I installed them. They work great, but the splash screen shows xubuntu, and apart from 'Last session', Xfce is now at the top of the sessions list on the login screen.
Does anyone know how to put this back to normal, without un-installing (permanently) kubuntu and xubuntu?
Thanks:grin:

P.S. If anyone finds my signature offending, please tell me.

---

### Post by scxtt on 2006-06-08
i don't really get what the problem is ... cause as i understand it, you should be able to have any windowing system installed and on the list - w/ the option of selection any of them (xfce, gnome, kde, enlightenment, etc.) and if that's different from your last session, gdm (at least) will ask you if you want to make your current session the default session (i.e. if you don't change sessions and you used gnome last, you'll always be using gnome until you select something else) ...

are you not getting this behavior?

---

### Post by aysiu on 2006-06-08
You can try this: ```
sudo apt-get remove kubuntu-artwork-usplash xubuntu-artwork-usplash
```

---

### Post by fazza on 2006-06-08
[QUOTE=scxtt]i don't really get what the problem is ... cause as i understand it, you should be able to have any windowing system installed and on the list - w/ the option of selection any of them (xfce, gnome, kde, enlightenment, etc.) and if that's different from your last session, gdm (at least) will ask you if you want to make your current session the default session (i.e. if you don't change sessions and you used gnome last, you'll always be using gnome until you select something else) ...

are you not getting this behavior?[/QUOTE]

I am getting that behaviour, but i prefer to keep the normal ubuntu bootup splash screen and have gnome as my (natural) default display manager. I know it sounds a bit picky, but I want to try to keep everything how it was when I installed it - I'm still learning about it and think that it's probably safer if I know where I'm at.
Thanks anyway
:)

---

### Post by fazza on 2006-06-08
will that mean that I keep my original splash?
cheers

---

### Post by urban on 2006-06-28
Hi fazza,

You might want to check out
```
man update-alternatives
``` 
e.g. 
```
sudo update-alternatives --config x-session-manager
```
to reset the system default session to gnome or whatever you prefer. 

This changes links stored in ```
/etc/alternatives
``` 
The reason for xfce getting preferred is, that xfce and gnome both have the same priority, but xfce seems to show up first in the relevant list of session-managers. update-alternatives gets executed automatically any time software is being installed or updated, which is known to the alternatives-system. We had the same behaviour since upgrading from breezy.

---

