---
title: "Replacing the Ubuntu menu icon"
date: 2006-08-03
forum: Desktop Environments
---

### Post by srunni on 2006-08-03
Hi,

I was trying to replace the Ubuntu menu icon (the one in the top left corner). I've already tried replacing that distributor-logo.png file. I tried editing the configuration manager (or whatever it's called). None of this worked. Are there any other ways to get it done?

Thanks.

---

### Post by ciscosurfer on 2006-08-03
The icon is located in your /usr/share/icons/NAME_OF_THEM_YOU_ARE_USING/THAT_YOU_WOULD_LIKE_TO_CHANGE

I would recommend backing up the current icon (copying) so that you can revert to it if you choose to do so.

The file you are looking for (provided you are using the Human icons) is located here:   /usr/share/icons/Human/24x24/places/start-here.png

You need to update you icon-cache for it to take:```
cd /usr/share/icons/
sudo gtk-update-icon-cache --force Human
```--force Human for the Human icon theme...replace that name with whichever icon theme you want to use your new icon with.

---

### Post by srunni on 2006-08-03
Will this change be system wide or only on one account?

---

### Post by srunni on 2006-08-03
Also, I'm currently using the T-ish theme. There is no /usr/share/icons/T-ish folder. And I have a .png that I want to replace the original with; it's not an entire theme.

---

### Post by ciscosurfer on 2006-08-03
The change will only effect you (not system-wide).

Go to your themes gui under System > Preferences > Theme and click on theme details then click the icons tabs.  Whichever one is highlited is your current icon theme.  Use this name to search under /usr/share/icons/*your_icon_theme.*

---

### Post by fabertawe on 2006-08-03
How bizarre... I couldn't find my icon theme's directory under '/usr/share/icons/' so I searched and found it in ~/.icons ! Now this is much easier to play with ;-)

Ubuntu 6.06 (Gnome) with the e16 WM.

Paul

---

### Post by srunni on 2006-08-03
I also have a ~/.icons . But now my picture next to "About Gnome" has been changed to what I want the menu icon to be. Do you know how I can change this back?

Also, can you post a copy of your /usr/share/icons/hicolor/48x48/apps/distributor-logo.png file (the original)?

---

### Post by srunni on 2006-08-03
Anyone know how to fix this?

---

### Post by ciscosurfer on 2006-08-03
Anything in your .icons directory is what's currently being used.

/usr/share/icons/Human/22x22/places is where my menu icon is located.  If you are using the Human theme then you can find your icons under the .icons directory (I don't use this theme...so my Human theme is located at the located at /usr/share....../places.

Also check [this thread]("http://ubuntuforums.org/showthread.php?t=26854").

Here is the distributor-logo.png (links to start-here.png) and the "About Me" icon (called user-info.png)

---

### Post by srunni on 2006-08-04
By the way, I found out that if I go to System -> Preferences -> Theme and mess around with it a little bit, then do a killall gnome-panel, it changes the menu icon to what it should be. Now I'm seeing how you change it back. I replaced the start-here.png file where it goes and where distributor-logo.png goes and I did that forced cache update, and then I went to Themes, messed around a little more. Now the "About Ubuntu" icon under System is what it should be, but the "About Gnome" and the menu icon are still what I changed them to.

---

