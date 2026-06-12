---
title: "unity program menu"
date: 2011-05-04
forum: Desktop Environments
---

### Post by JakeFrederix on 2011-05-04
Is it possible to put the menu and main interface of a program back together again?
I don't like this splitup that Unity does.

_first experience with Unity:_
I open pidgin instant messenger
I search in vain for a menu, looking where I can enable my accounts.
Thinking "It just isn't there. It used to be right here, a menu atop the program"
* few moments later *
Oh it's on top of the screen now.

To me, that is not convenient.
It's like entering a copy-shop, putting your papers in the machine, and then being told the machine controls are in the building further down the street.

So, is it possible to change/customize this option?

Kind regards,
Jake

---

### Post by Frogs Hair on 2011-05-04
Select Classic Gnome at login below the greeter box on the panel and the familiar desktop will appear.

---

### Post by werewolves on 2011-05-04
Do you mean the usual "File | Edit" menu that used to be at the top of the window, but is now on the top bar?

I don't think there is a way to customize that.

My advice is to try it for a while.  I thought I was going to hate it, but then I realized I can just sort of "toss" my mouse toward the top of the screen whenever I need the program menu.  I don't have to be precise, and it is alway in the same spot.  Once I got used to it, I felt it was much more efficient.  Just my two cents.

---

### Post by JakeFrederix on 2011-05-04
> **Frogs Hair said:**
> Select Classic Gnome at login below the greeter box on the panel and the familiar desktop will appear.

Not exactly what I had in mind. From what I understand Gnome is doomed to die soon. I would prefer to change Unity to my taste than to use something that I only enjoy for a limited time.

Also, on closer inspection of my login-screen it turns out I don't have that option.
I can see the time, the universal access button, and the shutdown button. The bar in bottom of the login screen does not contain other stuff for me.

---

### Post by mc4man on 2011-05-05
Well you could disable the global menu (several threads on) or disable it only on apps where not wanted.

To do that you need to open the app's desktop in a text editor and amend the Exec= line

For gtk apps - adding the blue as shown. ( orig line was
> Exec=pidgin

Ex.  - pidgin
```
gksudo gedit /usr/share/applications/pidgin.desktop
```
```
[Desktop Entry]
Name=Pidgin Internet Messenger
GenericName=Internet Messenger
Comment=Chat over IM.  Supports AIM, Google Talk, Jabber/XMPP, MSN, Yahoo and more
Exec=[COLOR="Blue"]env UBUNTU_MENUPROXY=0 [/COLOR]pidgin
Icon=pidgin
StartupNotify=true
Terminal=false
Type=Application
Categories=Network;InstantMessaging;
X-Ubuntu-Gettext-Domain=pidgin
```

Also if wishing a systray icon for pidgin then adding to the systray-whitelist will do (also enabling in pidgin's preferences

2 ways there - either manually adding in dconf-editor (install dconf-tools) or using gsetting - not hard to do once you get the idea

---

