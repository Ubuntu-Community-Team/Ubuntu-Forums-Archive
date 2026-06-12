---
title: "Can't get XFCE Power Manger to Autostart"
date: 2010-01-28
forum: Desktop Environments
---

### Post by pajamabama on 2010-01-28
There's an issue with the gnome-power-manager such that it doesn't detect when the AC Power is unplugged on my Aspire One.  It's described here [URL="https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/393008"]https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/393008
[/URL] 
The best workaround so far is to just use the xfce4-power-manager instead which works perfectly.  Unfortunately, I can't seem to get it to autostart at login.  Using the 'Startup Applications' control panel I've selected it to run at startup but it never seems to work.

Can someone suggest why this might be or another way to get it to work?

Thanks.

---

### Post by Brandon Williams on 2010-01-30
I assume that you're trying to run xfce4-power-manager in XFCE. When you install xfce4-power-manager, it installs /etc/xdg/autostart/xfce4-power-manager.desktop, which should already be enough. As installed, it will only run in XFCE, but as I say, I assume that you're running it in XFCE.

---

### Post by pajamabama on 2010-01-30
No, I'm running it in the default Ubuntu Netbook Remix which is Gnome.  I ended up just adding a .desktop file for it in /usr/share/gnome/autostart/ and it's working now.

As described in the bug report listed above, the gnome-power-manager doesn't detect the presence or absence of the AC adapter.  The XFCE one does.  And it works in the Gnome panel just fine.

Thanks for your help.

---

### Post by Brandon Williams on 2010-01-31
Glad it's working.

FWIW, the reason why /etc/xdg/autostart/xfce4-power-manager.desktop doesn't start the program when you run gnome is the presence of this line:
```
OnlyShowIn=XFCE;
```

You method works. I would have recommended that you do this instead:
```
[ -d $HOME/.config/autostart ] || mkdir $HOME/.config/autostart
grep -v OnlyShowIn /etc/xdg/autostart/xfce4-power-manager.desktop > $HOME/.config/autostart/xfce4-power-manager.desktop
```

This copies the installed .desktop file to your user's config directory, which overrides the installed one, removing the part of the file that prevents it from being used for a GNOME session.

---

### Post by pajamabama on 2010-01-31
I think I like that better.  I'll give it a try. Thanks.

:D:D

---

