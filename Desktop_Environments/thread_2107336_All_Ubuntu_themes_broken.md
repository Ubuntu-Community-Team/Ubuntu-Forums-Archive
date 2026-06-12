---
title: "All Ubuntu themes broken"
date: 2013-01-21
forum: Desktop Environments
---

### Post by AIPHEE on 2013-01-21
Hi, 
i have this problem, my menus are ugly and text have weird backgrounds, i think it appeared after installing pantheon desktop, now its purged but problem remains.
Appears in all themes.

Anyone knows how to fix it? 

Screen: [http://ubuntuone.com/2QYvdAqvKufuuXb2tbp0gD](http://ubuntuone.com/2QYvdAqvKufuuXb2tbp0gD)

---

### Post by Frogs Hair on 2013-01-21
Did you change file managers when trying the other desktop ?  You can make sure nautilus default in dconf editor. the path is org > gnome > nautilus > desktop and on the bottom default should read true. Nautilus helps draw the desktop themes in Gnome. If it is default try ```
nautilus -q 
```

---

### Post by AIPHEE on 2013-01-22
Dconf and command dindt helped. 
I Changed desktop few times, I used KDE for long time, but i really think this happened after installing patheon.

---

### Post by Frogs Hair on 2013-01-22
That is why I wondered about the file manager because pantheon has its own. Make sure the file manager is set to handle the desktop in the Gnome Tweak tool and if have the synaptic package manager installed check for installed auto removable packages it will appear on the left side when status is selected.

---

### Post by AIPHEE on 2013-01-22
Everything checks... IDK, doesnt seem tha FM can do that.

---

### Post by Frogs Hair on 2013-01-22
You can try the following.  
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by AIPHEE on 2013-01-23
Nothing...

---

### Post by Frogs Hair on 2013-01-23
What Graphics card and driver ? ```
lspci -v
```

---

### Post by stinkeye on 2013-01-23
Sounds like you may have a hidden config file in your home directory
overriding certain theme settings.
One program I use to customize theme colours creates a ~/.config/gtk-3.0/gtk.css file.

Do you have a **~/.gtkrc-2.0** or **~/.config/gtk-3.0/gtk.css** file.
If so, try moving them to your desktop and log out/in.

---

### Post by AIPHEE on 2013-01-24
My drivers are fglrx from xorg-edgers.

I have neither of those hidden files.

I yield, but i found theme which makes my desktop looks not ugly even with this weird theme bug.

---

### Post by Frogs Hair on 2013-01-24
Check for a Pantheon folders in home/hidden .config and delete it . I think stinkeye is on the right track.

---

### Post by AIPHEE on 2013-01-30
This helped: [http://askubuntu.com/questions/153376/broken-gtk-theme](http://askubuntu.com/questions/153376/broken-gtk-theme)

purging those 2 PPAs.

---

