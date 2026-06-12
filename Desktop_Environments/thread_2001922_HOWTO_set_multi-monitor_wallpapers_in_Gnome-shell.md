---
title: "HOWTO: set multi-monitor wallpapers in Gnome-shell"
date: 2012-06-11
forum: Desktop Environments
---

### Post by fatalGlory on 2012-06-11
I've recently switched over to gnome-shell on both desktop on laptop.  I hit a few usability hurdles, but have overcome most of them, so I thought I'd share some knowledge here (since I know many people have this same question).  Gnome-shell uses Nautilus to manage the desktop.  Nautilus only allows you to set a single wallpaper to use on both monitors, which is a bit unfortunate.  To fix this, we first have to tell Nautilus not to manage the desktop.  To do this install Gnome-Tweak-Tool:
```
sudo apt-get install gnome-tweak-tool
gnome-tweak-tool
```

After running gnome-tweak-tool, go to the "Desktop" tab in the left-side panel and then turn off the setting "Have file manager handle the desktop".

Next install Nitrogen (our new wallpaper-setting application):
```
sudo apt-get install nitrogen
nitrogen
```

Nitrogen allows you to pick wallpapers from your hard-drive and set them to individual monitors, etc.  To make sure that these wallpapers are restored after you reboot or logout, we need to tell Gnome to run **nitrogen --restore** at startup.  To do this, run:
```
gnome-session-properties
```

Here you can add a new startup program.  In the command box, enter "nitrogen --restore".  This will cause nitrogen to be run at startup and your most recent wallpapers to be shown on the desktop.

Hope this helps someone :)

---

### Post by Leslie Viljoen on 2012-07-08
This sure did help me, thank you very much!

---

### Post by orbitaldecay on 2012-11-12
Thanks!

---

### Post by molejo on 2013-03-08
> **fatalGlory said:**
> 

Hope this helps someone :)

It really did! I had some things done, but not working - thanks to your instructions I quickly got solution, because I was doingit wrong ;)

thanks again :D

:)

---

### Post by De Rinus on 2013-06-06
Open gnome-tweak-tool and go to Desktop.

Set "Picture Options" to "Wallpaper".

This would stretch my wide wallpaper over 2 screens.

I didn't need to install nitrogen or tell gnome to run nitrogen --restore every time i log in.

---

### Post by mind_exploit on 2013-06-07
> **De Rinus said:**
> Open gnome-tweak-tool and go to Desktop.

Set "Picture Options" to "Wallpaper".

This would stretch my wide wallpaper over 2 screens.

I didn't need to install nitrogen or tell gnome to run nitrogen --restore every time i log in.

I don't see such "Picture Options" ... :( ... 
I'm on OpenSUSE 12.3, Gnome 3.6, installed just yesterday ...

---

### Post by cincinnatus13 on 2013-06-07
^It's a feature in Gnome 3.8. You need to upgrade to get it (could add the Gnome repo if necessary probably on Suse.)

---

### Post by Adam_Newman on 2013-10-13
You can also do this by launching dconf-editor and navigating to org/gnome/desktop/background and change picture-options to "spanned"

---

