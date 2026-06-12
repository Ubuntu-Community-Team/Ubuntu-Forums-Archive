---
title: "Xfce Window Manager (???)"
date: 2005-05-20
forum: Desktop Environments
---

### Post by sameat on 2005-05-20
I'm confused...I have been using Xfce and loving it, but all of the sudden (after a reboot), I noticed that my wallpaper was the default Gnome wallpaper, and when I right click on the desktop, I get the gnome menu (instead of Xfce).

If I launch gnome and change the wallpaper, it changes in Xfce as well.  

The Panel and taskbar in Xfce seem to be working as expected, but I can't use the Xfce settings manager to change my wallpaper (I haven't tried anything else yet).

What did I do, and how can I undo it?

Additional info:  This also happened when I opened a vnc session on my kubuntu box...it launched KDE but had gnome wallpaper and rt click menu.  I don't do the vnc thing anymore, so I didn't bother fixing it.

Thanks!

---

### Post by bored2k on 2005-05-20
Here is the thing: you are **probably** opening up nautilus. Nautilus can and will take over your desktop. You need to open it with the nautilus --no-desktop parameter so it doesn't do this. You could also tweak this using cog [gnome configurator found in gnomefiles.org), gtweakui (apt-get) or just using the configuration-editor gconf.

---

### Post by sameat on 2005-05-20
Thanks for the quick response.  You were right, I did launch nautilus once, but I won't make that mistake again (xffm is good enough).

I did a "killall nautilus" and logged out, but now I have no rt click menu, and I still can't change my wallpaper.  Any ideas on how to undo the damage?

Thanks!

---

### Post by bored2k on 2005-05-20
[QUOTE=sameat]Thanks for the quick response.  You were right, I did launch nautilus once, but I won't make that mistake again (xffm is good enough).

I did a "killall nautilus" and logged out, but now I have no rt click menu, and I still can't change my wallpaper.  Any ideas on how to undo the damage?

Thanks![/QUOTE]
 Can't you change it from the xfce settings manager ? [display or desktop option I don't remember].

---

### Post by sameat on 2005-05-20
No...it doesn't seem to be working anymore.  Specifically, the wallpaper just doesn't change.  I also can't find the setting for the desktop context menu.

---

### Post by Xian on 2005-05-20
[QUOTE=sameat]I did a "killall nautilus" and logged out, but now I have no rt click menu, and I still can't change my wallpaper.  Any ideas on how to undo the damage?[/QUOTE]
You might try renaming the hidden xfce folder in your home directory (/home/<your_name>/.xfce) and empty your /tmp folder, then login again.

---

### Post by kangur on 2005-05-20
run: "xfwm4". (put it into terminal or command line on panel). Then restart xfce4.
If you save session ever, you will see opened "xfwm4".

---

### Post by psychicdragon on 2005-05-22
You need to start xfdesktop.

---

### Post by dust on 2005-05-24
[QUOTE=psychicdragon]You need to start xfdesktop.[/QUOTE]
 aye, just open a terminal and type xfdesktop. then logout and make sure that "Save session" is checked. Log back in and you're gold. btw, the whole nautilus taking over the desktop by default is fecking stupid.

---

### Post by Psquared on 2005-05-27
So -- with the, "nautilus --no-desktop" command if you run Nautilus in another desktop it will not take over?? This setting needs to be changed while in a Gnome session?

Thanks.

---

### Post by bored2k on 2005-05-27
[QUOTE=Psquared]So -- with the, "nautilus --no-desktop" command if you run Nautilus in another desktop it will not take over?? This setting needs to be changed while in a Gnome session?

Thanks.[/QUOTE]
 sudo apt-get install gtweakui
Systems > Preferences > Gtweak nautilus 
There you can make it NOT draw the desktop.

---

