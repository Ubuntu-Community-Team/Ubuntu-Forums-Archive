---
title: "permanently visible application file menu"
date: 2013-03-14
forum: Desktop Environments
---

### Post by BcRich on 2013-03-14
Hi,As much as I like Unity, I'm just not quite sure about the dissappearing Application file menu. I mean I don't really follow the logic is one supposed to memorize what drop down menu's are available for each application, until mouse overing the global menu?either way I'd like to know if it is possible to make the file menu's permanently visible for all applications that use the global menu?  these guys [http://askubuntu.com/questions/25785/can-auto-hide-for-the-application-menu-be-turned-off-in-unity](http://askubuntu.com/questions/25785/can-auto-hide-for-the-application-menu-be-turned-off-in-unity) seem to think that having to install the mentioned PPA is necassary  ppa:ikarosdev/unity-revamped.Is this the only way?And if so, has anybody reading this thread used this PPA is it stable enough for using on a production machine?thanks :)I'm using 12.04 x64 with standard Unity

---

### Post by vanadium on 2013-03-14
[edit]Rereading your question, I realize that you would prefer for the menu to remain in the top bar, but to be visible at all times. The instructions below remove the global menu and return the menus to the individual program windows.

A safe way to completely disable the global menu is by uninstalling the related packages:
```

sudo apt-get autoremove indicator-appmenu appmenu-gtk appmenu-gtk3 appmenu-qt

```

To revert to global menus, install the packages again
```

sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu

```

Although it will make no difference in your user experience, you could save small amounts of memory and an unperceptible gain in performance by disabling the "Global menu bar integration" plugins in Firefox and Thunderbird (just for the purists).

---

### Post by BcRich on 2013-03-14
Thanks for the reply vanadium,
yes I see what you're saying, however this will indeed remove the global menu. So just to be clear, I'd like to keep the global menu (simply because I think it's a useful feature) but just make all drop down menu headings (eg. File, Edit, Help etc) permanently visible for the active application. This is just so that I do not have to randomly hover my mouse towards a general direction hoping it will land up over the menu item I'm trying to access ;)
Thanks again for your help, it's very much appreciated!

---

### Post by Frogs Hair on 2013-03-14
There appears to be a remedy for 12.04 at the link. I have not tried this PPA though. [http://www.webupd8.org/2012/07/disable-global-menu-autohide-behaviour.html](http://www.webupd8.org/2012/07/disable-global-menu-autohide-behaviour.html)

---

