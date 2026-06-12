---
title: "Gnome Desktop Wallpaper Chooser"
date: 2005-04-21
forum: Desktop Environments
---

### Post by audax321 on 2005-04-21
Hello,

      I noticed that when opening the Desktop Preferences to change the wallpaper in ubuntu, it automatically updates and adds the wallpaper located in /usr/share/backgrounds

I keep most of my wallpaper though on a separate drive mounted at /media/windows and the wallpaper is kept in two directories (one for single screen wallpaper and the other for dual screen wallpaper)... is there a way to have the Desktop Preferences use these folders as a source as well?

Thanks  :)

---

### Post by TravisNewman on 2005-04-21
You CAN move all the backgrounds to the directory that you have most of your wallpapers already, remove /usr/share/backgrounds directory, and then ln -s /media/windows/path/to/wallpapers /usr/share/backgrounds

Then any wallpapers that get installed will go to your directory on /media/windows, and your desktop wallpaper changer will update with them.

---

### Post by audax321 on 2005-04-21
I had another idea just now... is it possible to instead link the individual files in the /media/windows/SingleScreen and /media/windows/DualScreen folders to /usr/share/backgrounds? That way, the /usr/share/backgrounds will contain any installed backgrounds and links to all the wallpapers in the other folders.

I remember there being a way to do this because I've done, just can't remember the proper way to format the ln command....

---

### Post by audax321 on 2005-04-21
Okay, I found the command, its just:

ln -s /media/windows/SingleScreen/* /usr/share/backgrounds

and it created the links... but the desktop chooser won't update itself.

I then tried it your way and got the same results....

I also tried to delete ~/.gnome2/backgrounds.xml and force Gnome to regenerate it but it only finds the Ubuntu wallpapers in the /usr/share/backgrounds folder and ignores everything else even if it is a regular file and not a link.

 I HATE Gnome's wallpaper manager...........  :mad:

---

