---
title: "transparency in gnome"
date: 2009-08-06
forum: Desktop Environments
---

### Post by wirate on 2009-08-06
How do I make window borders, menus and others transparent? I've been looking around and posting on other threads but no one gave me a complete reply. Yes I have compiz and Im new. I need steps :)

---

### Post by VCoolio on 2009-08-06
Go to compiz config settings-manager (in system > preferences; if it isn't there install the package compizconfig-settings-manager), then activate the "Opacity, Brightness and Saturation" plugin. Click and adjust the entries at will, eg for windows add Menu | PopupMenu | DropdownMenu and for value add 80.

For the window decorations to be transparent I think you'll need themes, especially emerald. Install emerald. Go to gnome-look.org and download beryl themes that have transparency. Open emerald theme manager (in system > preferences) and install themes by pointing to the (extracted?) theme. Select the theme. If your window decoration doesn't change do one of these:

1. run "emerald --replace" (don't know if that saves for next session)
2. in compiz settings, window decoration plugin, add in "command" entry: emerald --replace
3. Install fusion-icon, run fusion-icon. It will be an icon in your system tray / notification area. Right click and choose emerald as window decorator. Add fusion-icon to your startup apps and you're good.

---

### Post by Marlonsm on 2009-08-06
**To make window borders transparent:**
You'll need emerald, to install it:
-Open the terminal (Applications > Accessories) and run this:
```
sudo apt-get install emerald
```

Now, you'll need to make it start every time you turn the computer on:
-Go to System > Preferences > Startup applications
-Add a new application, name it Emerald and set the command as:
```
emerald --replace
```

To get it running, all you need to do is to log out and log in again.
To get themes for it, go here: [http://www.compiz-themes.org/index.php?xcontentmode=103](http://www.compiz-themes.org/index.php?xcontentmode=103)
To change the setting and install the new themes, go to System > Preferences > Emerald Theme Manager

**To make Menus, tooltips and others transparent:**
Open System > Settings > CompizConfig Settings Manager
Go to Opacity, Brightness and Saturation (check it)
In the Opacity tab, in Window specific settings, click "new".
This one is for the menus:
-Put windows like this:
```
(type=Menu | PopupMenu | DropdownMenu)
```
-and set a value, I use 75

And now for tooltips:
-Put windows like this:
```
(type=Tooltip | Notification)
```
-and set a value, I use 60

Optional: **Make transparent parts of the window blur what's behind them**
In CompizConfig Settings Manager, go to Blur Windows (and check it)
Check Alpha Blur
You can put whatever you want in the settings, I use Gaussian Blur, with Gaussian radius set to 10 and Gaussian strength set to 1.

Now, you can change whether this blur affects windows borders or not:
-Go to Emerald Theme Manager
-In the Emerald setting tab, change the value in "Compiz Decoration Blur Type"
Use "All decoration" to make window borders blur what's behind them or "None" if you don't want them to blur.

---

### Post by wirate on 2009-08-06
does emerald enable transparency only in window borders? I mean what if I want the thing transset sets to window to be set by default and for every window I open?

---

### Post by wirate on 2009-08-07
I figured that out. go to CompizConfig settings manager. Open opacity, brightness and saturation, enable it, click new button, type :"type=normal" and set the value.

---

### Post by Alma-Lover on 2009-08-10
i know it's a change of topic but i am running compiz and i had it on another computer which due to age has died....i had found a good tutorial that had window classes for opacity settings....however when i checked the HDD of that computer the bookmark to that tutorial takes you somewhere that says something "someone else has the domain name or some stupid **** like that"....so if anyone knows the classes or w/e theyr'e called for the active window and innactive windows that would be awesome....since active and innactive window didn't seem to work in the entry in brightness, opacity.....thing in compiz....

ty.....

---

### Post by mcduck on 2009-08-11
> **Alma-Lover said:**
> i know it's a change of topic but i am running compiz and i had it on another computer which due to age has died....i had found a good tutorial that had window classes for opacity settings....however when i checked the HDD of that computer the bookmark to that tutorial takes you somewhere that says something "someone else has the domain name or some stupid **** like that"....so if anyone knows the classes or w/e theyr'e called for the active window and innactive windows that would be awesome....since active and innactive window didn't seem to work in the entry in brightness, opacity.....thing in compiz....

ty.....

There aren't any classs or other window hints to make difference between active/inactive windows.

If you want to make active window opaque and inactive windows transparent, use the Trailfocus-plugin.

---

