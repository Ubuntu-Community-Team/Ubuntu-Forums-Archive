---
title: "Changing Ubuntu logo"
date: 2005-11-28
forum: Desktop Environments
---

### Post by spencer on 2005-11-28
Hi, I've read the following thread:

[http://ubuntuforums.org/showthread.php?t=26854]("http://ubuntuforums.org/showthread.php?t=26854")

I'm using a Mac os theme and would like to add an apple logo.png in place of the Ubuntu logo. Can I do it using the following method? Thanks! Using Breezy Badger.

-spencer

---

### Post by Kyral on 2005-11-28
Should be possible. Just sub in your gfx whereveer needed

---

### Post by spencer on 2005-11-28
It's not working for me, still have the Ubuntu logo. Where do I add in the apple.png?

Used these commands:

```
sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png
```

And 

```
sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/icons/Gnome-Apple/48x48/apps/gnome-main-menu.png
```

Did sudo killall gnome-panel and tried a different theme too. Still have Ubuntu logo. I also changed perimissions for the folder the Ubuntu logo is in and replaced with apple.png logo but it still shows Ubuntu logo. Can somebody correct me on this? Thanks!

-spencer

---

### Post by Hairy_Palms on 2005-11-28
thats the old hoary logo location the logo is now in 
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

---

### Post by spencer on 2005-11-29
Thanks Hairy_Palms! That was the fix. :D 


```
sudo cp /share/icons/Gnome-Apple/48x48/apps/gnome-main-menu.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```

I now have the Apple logo. Thanks!

-spencer

---

