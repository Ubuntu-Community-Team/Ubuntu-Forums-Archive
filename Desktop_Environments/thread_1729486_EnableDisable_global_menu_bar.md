---
title: "Enable/Disable global menu bar"
date: 2011-04-15
forum: Desktop Environments
---

### Post by adityakavoor on 2011-04-15
Hi,

In Natty beta, how do I enable or disable the global menu bar?

I used it for a while and got used to it. Then I pressed something (I don't know what) and the global menu bar disappeared and the menu now locally appearing in all windows. 

How do I enable it back?

---

### Post by chrestomanci on 2011-04-15
See [bug 734325](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/734325) in launchpad

It looks like the Ubuntu developers are digging their heels in and are determined that the global menu bar will be the new Coke for Ubuntu. They are refusing to provide a way to turn it off, as they believe it to be the future.

Personally I hate the global menu, so unless the situation changes, I will be switching Distro, probably to Debian or Mint.

---

### Post by coffeecat on 2011-04-16
@adityakavoor, the global menu is a panel applet in the classic gnome desktop. If you  want to disable it in the classic desktop, right-click on it and "Remove from Panel". If you  want to re-enable it, right-click on the panel > Add to panel >  Indicator Applet Appmenu.

> **chrestomanci said:**
> It looks like the Ubuntu developers are  digging their heels in and are determined that the global menu bar will  be the new Coke for Ubuntu. They are refusing to provide a way to turn  it off, as they believe it to be the future.

Disabling the global menu in Unity doesn&#8217;t seem to be an option though. This is true.

---

### Post by skiss on 2011-04-29
One way to enable/disable it is by installing or removing 2 packages:
indicator-appmenu appmenu-gtk 
(e.g.: sudo apt-get remove indicator-appmenu appmenu-gtk)

This will take affect next time you log in.

-Sandor

---

### Post by practic on 2011-05-02
According to WebUpd8:

Uninstall it:

sudo apt-get remove appmenu-gtk indicator-applet-appmenu indicator-appmenu

Then log out and log back in.

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

Also, to just disable it for an application, or all applications, so that you can easily re-enable it again:

[http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)

Personally, it is the only feature I'm not really fond of in Natty (and like some others said, I never really liked it on the Mac either)...although I think it will be good on my netbook. So I've removed it on my desktop computers.

---

### Post by r_mano on 2011-05-06
I agree... it is nice for a small screen, but the normal panel is much better for bigger screen. The ideal behavior, for me, is global menu when the app is maximized, and local menu when not. 

Moreover, the global menu has a tendency to disappear completely. I do not know exactly where to report it, but for example now I have gimp and digiKam without menus (nor global nor local) and the only way to recover is logout/login. Bump. 

I am checking KDE at home...

---

### Post by practic on 2011-05-06
I'm not sure if this will work for your global menu problem, but I've fixed a few things by clicking Alt-F2 (or opening a terminal if that doesn't work), and typing "unity" (without the quotes), then press Enter. It seems to reload the Unity launcher and panel, and sometimes fixes problems without having to logout/login.

---

### Post by fmmarzoa on 2011-12-06
practid, that FROZEN MY DESKTOP, so I think it's not a good idea in some cases (perhaps due nvidia propietary driver, in my case).

---

