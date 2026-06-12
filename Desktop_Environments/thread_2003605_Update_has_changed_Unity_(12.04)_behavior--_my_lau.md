---
title: "Update has changed Unity (12.04) behavior-- my launchers aren't grabbing windows"
date: 2012-06-14
forum: Desktop Environments
---

### Post by Dngrsone on 2012-06-14
In [this thread](http://ubuntuforums.org/showthread.php?t=1961681), in particular, I was exploring the ways launchers do and do not work in Unity.

Now something has changed.

The Unity bar no longer reflects the average color of the wallpaper, which isn't a big deal... yet. But also, the launchers I created for my different Firefox profiles are no longer grabbing hold of the windows they launched-- the 'default' Firefox launcher owns them now, and if I go to a different desktop, the launcher will open up either the instance in that desktop or the last instance used.

Any ideas what happened?

---

### Post by Dngrsone on 2012-06-16
Launchpad request: [https://answers.launchpad.net/launchpad/+question/200613](https://answers.launchpad.net/launchpad/+question/200613)

---

### Post by Dngrsone on 2012-10-31
I can verify it is fixed in Firefox 17 on Ubuntu 12.04 64-bit.
Example launcher code:

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/dngrsone/.icons/Daily.gif
Name[en_US]=Daily
Exec=firefox -no-remote --class Daily -P Daily
Name=Daily
Icon=/home/dngrsone/.icons/Daily.gif

---

