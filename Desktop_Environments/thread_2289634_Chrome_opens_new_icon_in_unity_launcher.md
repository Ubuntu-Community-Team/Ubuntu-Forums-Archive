---
title: "Chrome opens new icon in unity launcher"
date: 2015-08-05
forum: Desktop Environments
---

### Post by stepheny on 2015-08-05
If I open Chrome via the Unity launcher and then open a new window and an incognito window they all open using the same icon with three arrows to indicate three windows are open. This is the same behaviour that all my other Unity launcher icons have. 

However if I right click on the Chrome icon and select Incognito window a new icon opens at the bottom of my launcher so that there are two Chrome icons. This is annoying. I have tried editing /usr/share/applications/google-chrome.desktop to no avail. Someone suggested adding ```
StartupWMClass=Google-chrome-stable
```to the [NewIncognito Shortcut Group], but that didn't work either.

Does anyone know what I need to do to have only one Chrome icon regardless of how many windows are open?

---

### Post by mc4man on 2015-08-05
The whole deal makes little sense. What works here is to either create a new .desktop in ~/.local/share/applications (smaller as don't need all the translation lines..
or cp from /usr/share/applications to ~/.local/share/applications

The key is to use a different name.

So here on 14.04 a  google-chrome-stable new install it  installs  /usr/share/applications/google-chrome.desktop

I  - 
first delete any & all .desktops that chrome may have dumped in ~/.local/share/applications
remove the icon from unity launcher
then - 
 ```
cp /usr/share/applications/google-chrome.desktop  ~/.local/share/applications/google-chrome-stable.desktop
```
Then open that location & drag to launcher, it works as expected.

Edit: if chrome provided /usr/share/applications/google-chrome-stable.desktop, then copy that with a new name like google-chrome1.desktop or whatever..

---

### Post by stepheny on 2015-08-08
Thanks a million. Your suggestion works a treat. This has been bugging me for a while as I use Chrome with Bumblebee on my laptop and could never see if an instance was open.

---

### Post by mc4man on 2015-08-08
Why such a simple difference makes the diff here seems  not be simple to see why..
Anyway it's likely the change would survive updates as ~/ usually trumps, if not,  it then  would be useful to figure out why.
(- if it does break on update  repeat process again as quick fix. Just use a different name than the installed one.

---

