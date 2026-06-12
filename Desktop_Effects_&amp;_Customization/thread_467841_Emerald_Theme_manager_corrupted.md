---
title: "Emerald Theme manager corrupted?"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by punky on 2007-06-08
Hi,

I installed Beryl+Xgl and all was fine. The shutdown buttons were missing so I altered my startxgl and startxgl.sh files with this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

```

My button's have returned but now the theme is really ugly. Emerald changes the titlebar decoration, but nothing else. The menus, icons are all different. I know this sounds pedantic, but I hope someone can explain what's going on as i'd like my old theme back. The new one is very harsh on the eyes, I'd like the original icons, etc that came with Ubuntu. I'd still like to keep using Beryl though.

To help show the different themes using the shutdown button, please see the attachment.

I have tried switching back to gnome, makes no difference.

Many thanx in advance.

---

### Post by Soybean on 2007-06-08
Actually, the title bar (and window borders) is all that Emerald is *supposed* to change. So this (probably) isn't an Emerald problem. 

The icons are set by your theme selection under System-Preferences-Themes. If you're looking for the theme that you had when you first installed, it should be the one called "Human." If not, there are a few other options there... hopefully you'll find what you're looking for. :) Note that these themes include title bars and window borders too, but that *part* of the theme will be overridden by Emerald.

As for explaining what happened, though, I have no idea. I don't really know how any of what you described would've caused your Gnome theme to change. :???: Good luck!

---

### Post by kpolice on 2007-06-08
Run gnome-settings-daemon after everything has started and if your theme comes back just add gnome-settings-daemon to your startup programs.

---

### Post by punky on 2007-06-08
Excellent... running that gnome-settings-daemon fixed it! (it was already on human theme)

Thanx for your help guys. :KS

One last quickie though. What does the gnome-settings-daemon do? Can find a man page for it or anything on google. Its name would imply its a process which enforces gnome settings?

---

### Post by kpolice on 2007-06-08
AFAIK it's the process that loads all your GNOME settings, for some reason sometimes it doesn't load when you run beryl at startup (it should be loaded automatically).

---

### Post by tritops on 2008-02-15
Hi all,
hope it's ok to re-open this thread, I tried running the gnome-settings-daemon command on terminal, my desktop settings goes back to its ok state. but the moment i exit my terminal session, it reverts back to default.  I notice that my desktop environment gets the error only from a cold boot.

Any idea if there's a config setting issue that I need to check? I installed ubuntu gutsy with default settings only and the firestarter firewall. nothing more.

thanks in advance for any help.

cheers
N

---

