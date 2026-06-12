---
title: "windows from other workspaces showing on taskbar in compiz fusion"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by Metallion on 2007-10-03
As the title says. I am using compiz fusion and the taskbar is showing the windows from all workspaces at all times. This is quite annoying since it really overcrowds my taskbar. Is there any setting to get rid of this? I looked but couldn't find it so far.

---

### Post by Metallion on 2007-10-04
bump :(

---

### Post by Rupertronco on 2007-10-05
That's not compiz, that's gnome. Right click where the taskbar starts, it should be two sets of vertical, dotted lines. 

Go to preferences and click "show windows from current workspace".

---

### Post by Metallion on 2007-10-18
So the problem is not compiz? One thing I forgot to mention is that I am using Kubuntu so I have KDE instead of gnome. I couldn't find this option in KDE's taskbar preferences.

I also noticed that even when I have a window in another workspace... it still shows in the first workspace on my workspace switcher on the panel.

---

### Post by explemonk on 2007-10-18
> **Metallion said:**
> So the problem is not compiz? One thing I forgot to mention is that I am using Kubuntu so I have KDE instead of gnome. I couldn't find this option in KDE's taskbar preferences.

I also noticed that even when I have a window in another workspace... it still shows in the first workspace on my workspace switcher on the panel.

KDE's default taskbar applet does not work fully with Compiz (at least KDE 3.5.7 and under--I don't know if this was fixed in 3.5.8 or not).  You need to install a patched version to get the full functionality.  The source is available [here]("http://www.kde-apps.org/content/show.php/taskbar-compiz+for+kde+3.5.7+with+colors?content=61169") and requires the packages libxt-dev, libqt3-headers, libqt3-mt-dev, and kdebase-dev to compile.

When it is installed, you can remove the taskbar from your panel and then add the taskbar-compiz applet in its place.

The pager (workspace switcher) *does* work with Compiz, but it has to be started after Compiz to work right (as does taskbar-compiz).

After Compiz is loaded you can reload the panel and applets by typing

```
dcop kicker kicker restart
```

in a terminal.

I used to have a script in my ~/.kde/Autostart folder that would start Compiz Fusion, then wait 10 seconds and restart kicker.  However, that method caused me no end of grief.  I would get system tray icons popping up in their own little windows on the desktop instead of staying in the tray where they belong.  Also, restarting the kicker when using any GTK system tray apps (like Pidgin) would make the icons just disappear and I had to restart the respective program to get them back.

I finally found a solution that works for me on an openSUSE forum:

First, I installed fusion-icon to have a tray icon to mange Compiz Fusion with.  There may be a .deb file around somewhere, but I just compiled it from the git repository.  Then I made a script in my ~/.kde/env directory called startcompiz.sh with the following contents:

```
#!/bin/sh
export KDEWM="fusion-icon"
```

Now when my session starts the normal KDE window manager doesn't start at all, just Compiz does.  The panel loads next and so taskbar-compiz and the pager work nicely and all my system tray icons behave as they should.  It was frustrating to get it working right but it's working wonderfully now.

---

### Post by neuromancer99 on 2007-10-21
> **Rupertronco said:**
> That's not compiz, that's gnome. Right click where the taskbar starts, it should be two sets of vertical, dotted lines. 

Go to preferences and click "show windows from current workspace".

I think it's a problem with compiz because the option you're mentionning doesn't work with compiz-fusion (I use a wall instead of a cube).

---

### Post by veda on 2007-10-26
I had the same problem.

You can solve it by reducing the number of workspaces to 1 in the advanced desktop effect settings -> general options -> desktop size.

---

### Post by kungfoofool on 2007-10-26
For clarification, go to the dialog mentioned above and set "Number Of Desktops" to 1. Leave the "Virtual Size" as is. That seemed to fix this issue for me.

---

### Post by neuromancer99 on 2007-10-26
> **kungfoofool said:**
> For clarification, go to the dialog mentioned above and set "Number Of Desktops" to 1. Leave the "Virtual Size" as is. That seemed to fix this issue for me.

Thanks I'll try that tonight.

---

### Post by neuromancer99 on 2007-10-27
Great, it seems to work. Thanks again !

---

