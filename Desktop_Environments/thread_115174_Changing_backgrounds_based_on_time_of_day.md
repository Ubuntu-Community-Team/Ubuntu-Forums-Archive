---
title: "Changing backgrounds based on time of day"
date: 2006-01-10
forum: Desktop Environments
---

### Post by brohan on 2006-01-10
This seems a bit odd, but I'm trying to find the background setter for GNOME so that I can set backgrounds depending on the time of day, I'm getting a bit tired of seeing my bright very nice background at night, and if I get a darker one I just get tired in the morning :P
I've tried xsetroot, though I'm not sure of the syntax and I broke my cursor's (I fixed it through the gui).
If you could send a few lines of shell script and a wink about setting cron up also that'd be fantastic.

---

### Post by JimmyJazz on 2006-01-10
```
gconftool-2 --set --type string /desktop/gnome/background/picture_filename "/home/path/to/wallpaper_file.jpg" 

```
that'll do the trick.

---

### Post by brohan on 2006-01-10
Thank you!
Now to get learn how to cron, I'll post my results once I'm done :D

---

### Post by JimmyJazz on 2006-01-11
[http://jimmyjazz.homeip.net:808/changewalltime]("http://jimmyjazz.homeip.net:808/changewalltime")

hey man I made this little python script for you tonight it will change your wallpaper like you are wanting just open it up in a text editor, edit the config part at the beginning, make it excutable, and then make it a Gnome startup app.
Works like a charm for me.

---

### Post by JimmyJazz on 2006-01-11
I'll try to write up a nice little GTK front end for this tommarow so you can choose additional features and wallpapers without having to manually edit the script.

---

