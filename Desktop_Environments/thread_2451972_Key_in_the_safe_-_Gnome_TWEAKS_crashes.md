---
title: "Key in the safe - Gnome TWEAKS crashes"
date: 2020-10-14
forum: Desktop Environments
---

### Post by bugbear6502 on 2020-10-14
After numerous application difficulties with Lubuntu on my 2008 Dell Vostro 1700 (4Gb RAM, Intel Core 2 Duo CPU T5470 @ 1.60GHz, SSD installed), I installed "straight" Ubuntu.

Most of my application difficulties have been resolved, but general interaction is a bit sluggish (which is why I've been running Lubuntu since 16.0 LTS).

I did a quick google for speed ups, and "turning off the bells and whistles" seems the way to go.

Sadly, "Gnome Tweaks", accessed via Activities, crashes on startup.

The only extension/module I've installed is "gnome-shell-extension-autohidetopbar" which I'm using along with setting "Hide Dash", so my apps can use all the pixels I've paid for.

How can I diagnose (and hopefully fix) Tweaks? It seems quite key to my progess.

   BugBear

---

### Post by bugbear6502 on 2020-10-14
Having tracked my way through the application Desktop file to the executable, I tried from the command line:

[COLOR=#0000cd][FONT=courier new]bugbear@bugbear-dell: gnome-tweaks 
bugbear@bugbear-dell: echo $?
0
[/FONT][/COLOR]
Nothing appeared on the screen. So I don't think it's "crashing". I think it's *deciding* to do nothing, for some reason I don't understand.

  BugBear

---

### Post by rbmorse on 2020-10-14
For testing, you could remove the gnome-tweaks package (sudo apt remove gnome-tweaks) and disable the other two shell extensions from the extension applet found on the activities screen(s).  When that's done, then log out of your current session and log back in. 

When you log in again the shell extensions will not be active and you can add them back one at a time, starting with gnome-tweaks, until you find the culprit.

---

### Post by bugbear6502 on 2020-10-14
The Extensions App shows 4 extensions:


[LIST=1]
[*]Desktop Icons
[*]Hide Top Bar
[*]Ubuntu AppIndicators
[*]Ubuntu Dock
[/LIST]

Clearly I can remove (2). I suspect I can remove (1).

Removing (3) and (4) sounds a bit more "interesting" than I'd like.

Any pointers?

   BugBear

---

### Post by bugbear6502 on 2020-10-14
OK. I "apt-get remove"d (1) and (2) and gnome-tweaks itself.

A reboot showed everything working OK, and the Extensions App still loaded, showing (3) and (4).

I "apt-get intall"d gnome-tweaks and launched it from Activities.

There was a long pause (with a spinning cursor), then it ... went away.

Launching it again reverted to the immediate quit behaviour, so I suspect the pause was a cache being re-populated after my changes.

gnome-tweaks behaviour from the command line is also unchanged.

So - no joy.

   BugBear

---

### Post by CelticWarrior on 2020-10-14
> [COLOR=#000000]general interaction is a bit sluggish (which is why I've been running Lubuntu since 16.0 LTS)[/COLOR]
You may want to try Ubuntu-Budgie or other lighter flavor. Gnome requires a powerful graphics that you don't have. And the problems with Lubuntu seems to have been cause by a release upgrade that was absolutely NOT recommended by the developers: Lubuntu 20.04 only with a fresh installation, not even keeping /home as it carries on potentially conflicting settings. So, backing up personal files and nuking the old installation is the way to go.

Anyway, even sluggish standard Ubuntu should work but with caveats and limitations that you don't need to endure. But in that case and before anything else make sure the system is fully updated:
```
sudo apt update && sudo apt full-upgrade
```

---

