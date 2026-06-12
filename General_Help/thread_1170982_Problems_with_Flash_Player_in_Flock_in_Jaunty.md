---
title: "Problems with Flash Player in Flock in Jaunty"
date: 2009-05-26
forum: General Help
---

### Post by charleskw on 2009-05-26
I recently discovered Flock internet browser, and love the idea, however I, for some reason, can't get the flash player to install. I've seen posts online telling me to copy the .so file from the firefox plugins folder for flashplayer, and paste it in the Flock folder for plugins, which I tried, however it wouldn't let me copy. I then noticed that this folder couldn't be edited any way by me. I right clicked, selected properties, and then clicked the tab that read "Permissions."  All of the buttons are fogged out, disallowing me from changing anything. At the bottom of the window there is a note that reads "You are not the owner, so you cannot change these permissions." Any idea on how I can change these permissions, or another way to install flash player in Flock?

ALSO:
When the banner appears at the top of the screen claiming to let you install it directly from that banner, it doesn't work.

---

### Post by zobcat on 2009-05-26
open a terminal and enter: 
```
sudo nautilus
```

Now you're in root. You should be able to make any file operations.

---

### Post by zobcat on 2009-05-26
Or try this:

Open a terminal and enter
```
sudo ln /usr/lib/adobe-flashplugin/libflashplayer.so  /usr/share/flock/plugins/libflashplayer.so
```

Then restart Flock.

---

### Post by hjacker on 2009-05-26
You need root privileges to copy system folders and files, which are given by SUDO command in terminal/konsole. If you prefer to use visual interface just start nautilus/dolphin with root privileges and do everything from this window. To open browser with root privs. press alt+F2(or open a terminal) and enter ```
gksudo nautilus
``` for Gnome or ```
kdesu dolphin
``` for KDE. You can also create an icon on one of your panels for such browser, so you can reach it easily next time you require it. That's it. I hope I got your question right.
And BTW what's the idea of Flock in brief?

---

### Post by hjacker on 2009-05-26
> **zobcat said:**
> Or try this:

Open a terminal and enter
```
sudo ln /usr/lib/adobe-flashplugin/libflashplayer.so  /usr/share/flock/plugins/libflashplayer.so
```Then restart Flock.

Is flash plugin universal? I saw a bunch of non-adobe flash plugins available, do they use same libraries?

---

### Post by zobcat on 2009-05-26
I was hoping that the OP has the default and best plugin from adobe installed. I guess I should have asked. But, in case you don't OP, then you need to get it. It's called adobe-flashplugin. Make sure to uninstall all other flash plugins (i.e. gnash, swfdec).

But, yes. It works on my machine.

---

