---
title: "Xubuntu Session vs Xfce Session"
date: 2013-01-16
forum: Desktop Environments
---

### Post by Clark Leach on 2013-01-16
Can anyone explain the difference?  I've logged in both ways and they look identical.  Why doesn't it look and act anything like linux mint w/Xfce?  Where the hell is the volume control?  Why are there only 3 apps (none of which I have heard of) in the system section of the app menu? 5,000,000 different versions of linux starts to make windoze look pretty good.

---

### Post by ajgreeny on 2013-01-16
> **Clark Leach said:**
> Can anyone explain the difference?  I've logged in both ways and they look identical.  Why doesn't it look and act anything like linux mint w/Xfce?  Why can't I move the task bar from the top to the bottom?  Where the hell is the volume control?  Why are there only 3 apps (none of which I have heard of) in the system section of the app menu? 5,000,000 different versions of linux starts to make windoze look pretty good.
I am not certain about the difference between a Xubuntu and an XFCE session, but have a look in the listed startup apps for both; they may me different, but I really don't know, though I agree they look exactly the same.

You can move the task bar from the top to the bottom, but if I remember correctly you will need to remove the panel which looks and acts like a dock from the bottom first.  I didn't like or use that panel anyway so got rid of it and moved the top panel to the bottom, in its place.  You will need to right click the panel first and unlock it in the properties dialog box, then drag it with the handle, (at the left hand end, I think).

Not sure about the three apps in the system menu, and I'm not on Xubuntu at the moment.  Remind me what they are, and tell me what you want.  You can always add anything extra that you want with the menu-editor from a right click on the menu button, I think.

---

### Post by Frogs Hair on 2013-01-16
When installed on Ubuntu  the session has far less packages than the Xubuntu desktop . The login screen, Abiword, and gdm are just some of the many packages and dependencies  excluded.

The xfwm4 4.10 window manager combined with the xfce-goodies are much lighter. It is easy to see what belongs to the session when installed on Ubuntu but without looking at the dependencies it would be difficult on Xubuntu.

---

### Post by Toz on 2013-01-16
> Can anyone explain the difference? I've logged in both ways and they look identical.The xubuntu session differs from the xfce session in that it applies some of the xubuntu-specific enhancements to Xfce (themeing, wallpaper, some config changes, etc). Have a look at the files in the xubuntu-default-settings package.

However, here is the caveat. The difference is only applied on your first login (when the ~/.config/xfce directory is created). If you select xubuntu session, you will get a different set of configuration options than if you choose xfce session. If, on the other hand, the ~/.config/xfce directory already exists, it won't matter which session you choose at login because it will start xfce and apply the settings that were created as a result of your original choice.

The best way to test and view the differences is to create two new accounts, and for one, select Xubuntu session and the other xfce session then compare. (You can also delete the ~/.config/xfce and ~/.cache/sessions folder between logins to reset xfce, but you will lose all customizations).

> Why doesn't it look and act anything like linux mint w/Xfce?If you want Linux Mint, you need to install Linux Mint. They probably use a different set of configuration options.

> Where the hell is the volume control?
In the xfce session, the volume control needs to be added manually.

> Why are there only 3 apps (none of which I have heard of) in the system section of the app menu?
Probably the default xfce system menu.

> 5,000,000 different versions of linux starts to make windoze look pretty good. 
You should use what works best for you. Some appreciate the wide diversity of and configuration options offered by Linux. Others don't.

---

### Post by Clark Leach on 2013-02-03
Thanks for the responses, everybody.

---

