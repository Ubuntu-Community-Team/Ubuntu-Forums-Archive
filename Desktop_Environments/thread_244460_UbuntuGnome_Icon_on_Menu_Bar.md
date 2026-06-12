---
title: "Ubuntu/Gnome Icon on Menu Bar"
date: 2006-08-26
forum: Desktop Environments
---

### Post by resolve on 2006-08-26
I know it's been asked many times, and yes, I have searched extensively on the forums and on google for a solution. Every solution I've found is old or doesn't work.

Basically, I want to change the icon from the Ubuntu icon to the normal Gnome foot icon.

Here's what I did so far:

[I]cd /usr/share/icons/hicolor/48x48/apps
sudo cp distributor-logo.png distributor-logo.bak
sudo cp gnome-main-menu.png distributor-logo.png[/I]

Here is what I get from doing that:

[http://img246.imageshack.us/my.php?image=menubarjo7.png](http://img246.imageshack.us/my.php?image=menubarjo7.png)

Basically, I can change the Main Menu back to the normal Gnome foot icon, but NOT the Menu Bar.  The part that confuses me, is what I did DOES change the Menu Bar icon in the Add to Panel window.

So, anyone have a solution to changing the Menu Bar icon to the Gnome foot?

---

### Post by kaamos on 2006-08-26
Hello!

The logo is theme specific and changing it in hicolor only affects icon themes that do not define distributor-logo.

```
**$ locate distributor-logo**
/usr/share/icons/Human/22x22/places/distributor-logo.png
/usr/share/icons/Human/24x24/places/distributor-logo.png
/usr/share/icons/Human/48x48/places/distributor-logo.png
/usr/share/icons/Tangerine/16x16/places/distributor-logo.png
/usr/share/icons/Tangerine/22x22/places/distributor-logo.png
/usr/share/icons/Tangerine/24x24/places/distributor-logo.png
/usr/share/icons/Tangerine/scalable/places/distributor-logo.svg
/usr/share/icons/Tango/scalable/places/distributor-logo.svg
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

```

Note: you might have update the theme. So do this for the theme you wish to change:
```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```

---

### Post by resolve on 2006-08-26
Thanks for the reply.

I saw all those when I was messing with it, but got a little confused. I'm not using any of those icon themes right now, so what would I have to replace...?

---

### Post by kaamos on 2006-08-26
You can see what icon theme you have in System->Preferences->Theme->Theme details->Icons. The theme can then be found at /usr/share/icons/*<name-of-theme>* or /home/*<username>*/.icons/*<name-of-theme>*. If you have a theme that does not use its own logo file, just changing the file in hicolor (as you have done) and running the update command in my last post should be enough. Otherwise, change the icon in the theme and run the update command for that themes location.

Hope this helps.

---

### Post by resolve on 2006-08-26
I missed the cache update part in your last post. Ran it and it works perfectly now.

Thanks!

---

