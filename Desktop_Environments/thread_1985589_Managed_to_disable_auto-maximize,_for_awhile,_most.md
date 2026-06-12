---
title: "Managed to disable auto-maximize, for awhile, mostly..."
date: 2012-05-23
forum: Desktop Environments
---

### Post by LeFou on 2012-05-23
I cannot stand auto-maximize and spent awhile finding the right way to get rid of it. But:

With Compiz setting window placement "smart" I still get auto-maximize when I switch between desktops. i.e.:

-launch firefox, size it the way I want. 
-switch to desktop 2, with thunderbird on it
-when switching back to desktop 1, firefox (and gnumeric, incidentally) are maximized again)

---

### Post by drs305 on 2012-05-23
Have you tried CCSM's Window Management, Grid, Edges > Resize Actions? Click the one(s) you want and select None. For instance, to prevent maximization when drag to the top, select "Top Edge" and 'none'.

Turning off "Grid" also corrects the automaximize issue but may have other changes you don't want to lose.

---

### Post by JRV on 2012-05-23
Do you have "Grid" unchecked in the Window Management section of ccsm?

This stops a window from auto-maximizing if it touches the top panel.

---

### Post by LeFou on 2012-05-23
> **drs305 said:**
> Have you tried CCSM's Window Management, Grid, Edges > Resize Actions? Click the one(s) you want and select None. For instance, to prevent maximization when drag to the top, select "Top Edge" and 'none'.

Turning off "Grid" also corrects the automaximize issue but may have other changes you don't want to lose.

This worked, Thanks. I changed a few edges' behaviors. Not sure which one corresponds to desktop-switching.

---

### Post by LeFou on 2012-05-23
Oh wait, it's doing it again. So I disabled Grid and Scale entirely.
It's still doing it.

Per the original post, it is not auto-maximizing when I move a window near the top, etc. It's doing it when I switch to desktop 2 and then back.

Is there a way to turn off auto-maximizing? There appears not to be, since "maximiz" entered in compiz settings search doesn't have any results.

---

### Post by LeFou on 2012-05-23
Oh, wait. With the "Advanced Search" I was able to find some more references to auto-maximize, including one in the Ubuntu Unity Plugin:
"Automaximize value" : "The minimum value to trigger auto-maximize"
I don't know what that means.

But I disabled Ubuntu Unity plugin to see if it helped. It didn't.

Can't be turned off I guess?

---

### Post by LeFou on 2012-05-23
With more searching and stuff I realized there are about a dozen threads full of people annoyed by this, ahem, feature. For me, the solution was installing gconf-editor and toggling the apps>metacity value

[http://ubuntuforums.org/attachment.php?attachmentid=211701&d=1327957573](http://ubuntuforums.org/attachment.php?attachmentid=211701&d=1327957573)

Page 4 of this thread:
[http://ubuntuforums.org/showthread.php?t=1746241&page=4](http://ubuntuforums.org/showthread.php?t=1746241&page=4)

has some nice detail about how sometimes it's the unity plugin (apps > compiz-1 > plugins > unityshell > screen0 > options > automaximize_value)  and sometimes it's now, plus sometimes it doesn't work right in ubuntu-2d, and so on.

In my opinion GRUB should start up like this

Ubuntu, with linux 3.0.0-12-generic (auto-maximize mode)
Ubuntu, with linux 3.0.0-12-generic (usable mode)
Ubuntu, with linux 3.0.0-12-generic (recovery mode)

---

### Post by drs305 on 2012-05-23
Sorry you haven't found a solution yet. You may get more assistance if you remove the SOLVED tag. It's reversible, so just use the same link you set it with.

---

