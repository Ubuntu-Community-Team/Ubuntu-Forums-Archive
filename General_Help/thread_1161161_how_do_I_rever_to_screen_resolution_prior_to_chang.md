---
title: "how do I rever to screen resolution prior to change?"
date: 2009-05-16
forum: General Help
---

### Post by mlanza on 2009-05-16
I recently changed the screen resolution from System > Preferences > Screen Resolution.  I wanted to try one of the higher resolutions and I figured, there's no hard to that.  In Windows if you switch and something goes wrong it automatically reverts after a few seconds.  This is not what happened to me.  The monitor (DELL 1907FP) displayed a message something to the effect that it couldn't display the video.  Now I am having an incredible headache trying to simply get the system to boot properly again.

Basically, it boots normally, eventually it switches to the desktop (just the colored background and not the wallpaper) for just a second and then the video fails (I am supposing right after it tries to switch into the higher resolution).

I have read many posts and tried all sorts of things unsuccessfully and am incredibly frustrated by the experience.  I have tried all sorts of things usually in TEXT mode (ALT + CTRL + F1): 

1) modifying /etc/X11/xorg.conf
2) running xrandr
3) attempting to boot to safe mode via GRUB
4) running sudo dpkg-reconfigure xserver-xorg

By adding a Modes "1024x768" to the xorg.conf I can usually get into Ubuntu temporarily, nevertheless, it doesn't resolve the issue.  Subsequent boots revert to the failed video.

Please, please, is there a simple way to resolve this issue.  I can't for the life of me see why experimenting with screen resolution should turn into a 3+ hour issue.

Thanks so anyone who can point me in the right direction.

Please see attached screenshot.

---

### Post by dcstar on 2009-05-16
> **mlanza said:**
> I recently changed the screen resolution from System > Preferences > Screen Resolution.  I wanted to try one of the higher resolutions and I figured, there's no hard to that.  In Windows if you switch and something goes wrong it automatically reverts after a few seconds.  This is not what happened to me.  The monitor (DELL 1907FP) displayed a message something to the effect that it couldn't display the video.  Now I am having an incredible headache trying to simply get the system to boot properly again.

Basically, it boots normally, eventually it switches to the desktop (just the colored background and not the wallpaper) for just a second and then the video fails (I am supposing right after it tries to switch into the higher resolution).

I have read many posts and tried all sorts of things unsuccessfully and am incredibly frustrated by the experience.  I have tried all sorts of things usually in TEXT mode (ALT + CTRL + F1): 

1) modifying /etc/X11/xorg.conf
2) running xrandr
3) attempting to boot to safe mode via GRUB
4) running sudo dpkg-reconfigure xserver-xorg

By adding a Modes "1024x768" to the xorg.conf I can usually get into Ubuntu temporarily, nevertheless, it doesn't resolve the issue.  Subsequent boots revert to the failed video.

Please, please, is there a simple way to resolve this issue.  I can't for the life of me see why experimenting with screen resolution should turn into a 3+ hour issue.

Thanks so anyone who can point me in the right direction.

Please see attached screenshot.

The user screen resolution settings are stored in the key values accessed by the Gconf editor in this hidden folder:

```
.gconf/desktop/gnome/screen
```

Use another login (or a Live CD) to rename the "screen" folder and then log in again.

---

### Post by CatKiller on 2009-05-17
> **mlanza said:**
> Please, please, is there a simple way to resolve this issue.  I can't for the life of me see why experimenting with screen resolution should turn into a 3+ hour issue.

The user's resolution setting is kept in ~/.config/monitors.xml.

---

### Post by Legace on 2009-05-17
> **CatKiller said:**
> The user's resolution setting is kept in ~/.config/monitors.xml.

Yeah, you should do
```
rm home/YOUR_USERNAME/.config/monitors.xml
```

(rm = remove)
in recovery mode (root shell).

---

### Post by CatKiller on 2009-05-17
Well, the OP doesn't need to be in recovery mode as he has access to the virtual consoles. Unless you put crazy values in there, it's also possible to just edit that file with ```
nano ~/.config/monitors.xml
``` Obviously, putting crazy values in there would be crazy. But yeah, removing the existing file and letting the system create a new one is probably quite straightforward. I'd be tempted to just rename it to something else, though, just in case. ```
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
``` I guess I'm just the cautious type.

---

