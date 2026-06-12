---
title: "Cannot right click on Gnome Desktop"
date: 2005-10-03
forum: Desktop Environments
---

### Post by xthaparian on 2005-10-03
Today When I booted Ubuntu then I saw a very peciliar problem. I cannot right click on my desktop and The desktop wallpaper which I installed is not there anymore.

So I went to the "Change background" option and it fires up and I cannot set the backgorund on the gnome. I can see the wallpapers but if I click on it, it is not setting the desktop.

Any feed back please??

Do I have to reintall Gnome?? if then how??

---

### Post by darkmatter on 2005-10-03
[QUOTE=xthaparian]Today When I booted Ubuntu then I saw a very peciliar problem. I cannot right click on my desktop and The desktop wallpaper which I installed is not there anymore.
So I went to the "Change background" option and it fires up and I cannot set the backgorund on the gnome. I can see the wallpapers but if I click on it, it is not setting the desktop.
Any feed back please??
Do I have to reintall Gnome?? if then how??[/QUOTE]

It's sounds like Nautilus is no longer drawing your desktop. Did you change any settings in the configuration editor?

Regardless, go to your applications menu. Under System Tools -> Configuration editor.

Use the left tree view to navigate to: apps -> nautilus ->preferences and make sure that the 'show_desktop' option IS CHECKED.

If it isn't, then check it and exit the Configuration Editor.

open a terminal and enter the command
```
nautilus
```

leave the terminal open.

Under System -> Preferences -> Sessions, select the Current Session tab, select nautilus and set the Order to 40, and set the Style to Restart. Hit Apply and then switch to the terminal window.

Close the terminal. Nautilus should exit and a new instance should start.

Close the Sessions window and log out, making sure to check the option to 'Save current setup'.

Log back in and you should have a fully functional desktop again.

Good Luck. If there are any more problems or if it doesn't work, post back and I'll try to help as best I can.

---

