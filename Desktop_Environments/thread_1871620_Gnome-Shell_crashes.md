---
title: "Gnome-Shell crashes"
date: 2011-10-29
forum: Desktop Environments
---

### Post by BazookaAce on 2011-10-29
Hi, 

I have some problems with Gnome Shell. At least two times a day Gnome Shell will crash without warning. When it crashes everything disappears, but i can still use the applications that are open, but i can't close/minimize/maximize them. The reason for that is that the top bar (with close/minimize/maximize buttons) disappears completely and i have to reboot my computer or log out (CTRL ALT DEL) if it allows me to do so (which is about 50% of the times).

I can't access the terminal either (my terminal shortcut is CTRL + < ). I suspect it's something with a extension or something, but all my extensions are updated and are supported by Gnome-Shell 3.2. 

Here are my extensions that currently is used: 

- User theme
- Extended Places Status Indicator
- Media Player Indicatior
- Application Menu
- Gimmie Extension
- Temperature Indicator
- Weather Indicator

Any thoughts? Thanks in advance.

---

### Post by typhoon_tip on 2011-10-29
To me it looks very similar to a problem I have in Unity when I am editing compiz settings. After a few restarts of Compiz, everything remain in the same status that you mentioned, and I have to reboot my computer because I cannot even logoff. I would suggest you to reset entirely your compiz profile and start back all over again.

---

### Post by BazookaAce on 2011-10-29
I'm not using Compiz, so it can't be it.

---

### Post by crdlb on 2011-10-29
If an extension is causing this, it's probably the user theme extension. There have been a lot of reports of third-party themes being buggy (or triggering bugs).

---

### Post by BazookaAce on 2011-11-03
Yup, haven't had any crashes since yesterday when i changed the theme to "Nord".

---

### Post by AvalonSpirit on 2011-11-03
My gnome shell only crashes when I change te theme to something other than default. It normally happens when i go into the activites overview and start typing.

So it probably is an extension. What i do when that happens to avoid having to restart the computer is hit   ctrl+alt+F1.

and login into tty1, display running gnome processes with:

```
ps x | grep gnome
```

and kill gnome-session:

```
kill -9 "process number"
```

where process number is the process ID (without the quotes)

This will return you to your login screen.

---

### Post by Frogs Hair on 2011-11-03
I have not had the shell crash , but the Salinx theme caused problems when logging out of the shell and into Unity . The theme was removed and so was the problem .

---

### Post by fredric_ on 2011-11-03
I have the same problem. I'll try changing the theme to "Nord"

---

### Post by typhoon_tip on 2011-11-03
Confirmed even in Unity, some themes for Gnome 3 / GTK 3 causes more damages than good. I have installed them and tested, and especially in one occasion it messed up Unity so badly I have to reset the entire thing (when minimizing and then restoring a full-screen window, the title bar will go under the top bar shifted up by at least 50 pixel over the edge of the screen, rendering the app not usable; ALT+F4 and re-open it, happened all the time with any maximized window ! Still some work to do ;) :) ).

---

### Post by BazookaAce on 2011-11-04
Well, that was that :p It crashed again with Nord :(

---

### Post by robbiemacg on 2011-11-04
I was having a similar issue until recently. My Shell would crash when I tried to restart it if I had extensions installed. I could run user themes no problem, but pretty much any extension crashed my gear.
As of last night, I'm all good. There were a couple of decent updates pushed out by the Gnome3 Team. Do you have the  Gnome3 Team PPA to your sources, so you can  continue to get updates, etc.? A lot of people seem to have initially  installed Gnome Shell via downloaded DEBs initally.
I'm sure you know what you're doing if you're experimenting with new environments and stuff, but it might be worth doing a quick:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

Pull down an update if you haven't in a while and see if it helps.

---

### Post by BazookaAce on 2011-11-05
Yeah i got the update, and i haven't experienced any crashes yet, so it looks like it's maybe fixed :D

---

### Post by chazdg24 on 2011-11-09
Looking forward to see if this solves my problem!  :D

---

### Post by chazdg24 on 2011-11-09
Yikes, I can't Gnome 3.2 to load at all.  I need to use Unity or Gnome Classic.  How do I fix this???

Thanks in advance.

---

### Post by smaegol on 2011-11-28
I have the same problem with Gnome-Shell. It crashes at least once in 2 days. I've also observed large memory consumption by the process gnome-shell, so I'm restarting gnome-shell from time to time to increase system stability.

My solution for going back to system functionality after crash is to open tty (alt + ctrl + F1), log in, then, after killing gnome-shell process (not gnome-session - it will log you out), I type in:

```
gnome-shell -d :0 --replace
```That opens gnome-shell on the standard X display (as indicated with -d :0). --replace option replaces existing window manager (if you didn't manage to kill gnome-shell). 

After that operation system doesn't look like normal, themes are not working, but you are able to safely close all applications and reboot computer without lost of your data.

---

### Post by Tornikee on 2012-02-03
I also experience the GNOME Shell freeze issue about once every day.

Using GNOME Shell 3.2.2.1

Shell theme *Hope*
Window theme *Orta*
GTK+ theme *Hope*

Extensions *Alternative Status Menu, AlternateTab, Trash, Music Integration, User Themes Extension, Removable Drive Menu, Frippery Move Clock*

---

