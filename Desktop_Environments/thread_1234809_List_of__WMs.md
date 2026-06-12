---
title: "List of  WMs"
date: 2009-08-08
forum: Desktop Environments
---

### Post by Bearded-flower on 2009-08-08
Hey i was just wondering if anyone knows any good WMs or DEs?
i have tried gnome, KDE, XFCE, fluxbox and Enlightenment. (this is probably me being a retard but using fluxbox and E i xouldnt figure out how to get into my networks thing, which is a dissapoinment cos i liked 'em)
i just wanna know ypur personal favoriutes etc.
any stories or anything and is there anything lightweight without looking hideously UGLY?

---

### Post by gjoellee on 2009-08-08
You should find what's good for you and not rely on other people's favorite DE or WM. But here is a list with a few of your possible choices:

**DE's:**
-KDE
-XFCE (lightweight)
-GNOME
-E17 (lightweight)
-E16 (lightweight)
-LXDE (Super lightweight)

**WM's:**
-Openbox (recommended WM)
-Fluxbox
-Blackbox
-FVWM
-IceWM
-Metacity (used in GNOME)
-Compiz (used for fancy effects)

I am not going to write down more...

---

### Post by harry2006 on 2009-08-08
i like fluxbox and xfce for DMs as i like to keep things simple and clean...anyways its a personal choice only.

---

### Post by Mark76 on 2009-08-08
> **gjoellee said:**
> You should find what's good for you and not rely on other people's favorite DE or WM. But here is a list with a few of your possible choices:

**DE's:**
-KDE
-XFCE (lightweight)
-GNOME
-E17 (lightweight)
-E16 (lightweight)
-LXDE (Super lightweight)

**WM's:**
-Openbox (recommended WM)
-Fluxbox
-Blackbox
-FVWM
-IceWM
-Metacity (used in GNOME)
-Compiz (used for fancy effects)

I am not going to write down more...

You could add FVWM-Crystal, Windowmaker/GNUStep and ROX Desktop to the list of DEs.

And you forgot KWin and XFWM in the window managers

---

### Post by flux_user on 2009-08-21
How do you get into Network Settings for gnome via fluxbox?

1) Bring up root menu (right click on desktop default)
2) Go to Applications:
3) Go to System
4) Go to Gnome Network Tool

Just a guess; but I don't think your menus were updated when you logged into fluxbox.  Your menus should have looked  something like this:

[http://customize.org/fluxbox/themes/64740](http://customize.org/fluxbox/themes/64740)
or
[http://customize.org/fluxbox/themes/64677](http://customize.org/fluxbox/themes/64677)

Now the  screenshot doesn't show the network tool but this should give you an idea of the menu structure that you should have seen.  If you didn't see the structure; then your menu's might need to be updated.  

**To summarise under a different window manager you may need to update your menus** for : fluxbox, openbox, blackbox, icewm etc.  Update your menus and try all your Window Managers again :-)  Pick the ones that you like.

PS: Disclaimer; yes, those are my screenshots  and themes that I created.  :-)

You can use the ***update-menu*** command if I am not mistaken.  You want to double  check on the forums in case I may be mistaken.  Better yet; post a question about updating your menus or updating your menus for your specific window manager.

Hope this helps.  :-)

---

### Post by flux_user on 2009-08-21
I forgot one thing:
**The SUPER SITE to Desktop Environments and  Window Managers:**

**[http://xwinman.org/](http://xwinman.org/)**

If it exists then it's in that list.

---

### Post by urukrama on 2009-08-21
My favourite are Openbox, and Musca. I also use and like Awesome (2.3) from time to time.

> **flux_user said:**
> I forgot one thing:
**The SUPER SITE to Desktop Environments and  Window Managers:**

**[http://xwinman.org/](http://xwinman.org/)**

If it exists then it's in that list.

That site is terribly outdated. There are *a lot* of window managers that are not in that list.

For a more complete and continually updated list, have a look [http://www.gilesorr.com/wm](http://www.gilesorr.com/wm)

---

### Post by coldReactive on 2009-08-21
> **gjoellee said:**
> You should find what's good for you and not rely on other people's favorite DE or WM. But here is a list with a few of your possible choices:

**DE's:**
-KDE
-XFCE (lightweight)
-GNOME
-E17 (lightweight)
***_[COLOR="Red"]-E16 (lightweight)[/COLOR]_***
-LXDE (Super lightweight)

**WM's:**
-Openbox (recommended WM)
-Fluxbox
-Blackbox
-FVWM
-IceWM
-Metacity (used in GNOME)
-Compiz (used for fancy effects)

I am not going to write down more...

E16 is considered a Window Manager.

---

### Post by 37fleetwood on 2009-08-21
Hi, I posted this some time ago, hope it helps. anyone wanting to add to it please feel free.

[http://ubuntuforums.org/showthread.php?t=1176747](http://ubuntuforums.org/showthread.php?t=1176747)

Scott

---

### Post by earthpigg on 2009-08-22
> **Bearded-flower said:**
> Hey i was just wondering if anyone knows any good WMs or DEs?
i have tried gnome, KDE, XFCE, fluxbox and Enlightenment. (this is probably me being a retard but using fluxbox and E i xouldnt figure out how to get into my networks thing, which is a dissapoinment cos i liked 'em)
i just wanna know ypur personal favoriutes etc.
any stories or anything and is there anything lightweight without looking hideously UGLY?

i had to find the workaround to get nm-applet (Ubuntu's default and *_outstanding_* network manager) to work outside of gnome and xfce for a project i am working on: [http://sites.google.com/site/masonux/](http://sites.google.com/site/masonux/)

```
sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/nm-applet.desktop #comment out the OnlyShownIn line of /etc/xdg/autostart/nm-applet.desktop to allow nm-applet to function outside of gnome and xfce.
```

that will open up the possibilities of nm-applet working in other WMs and DEs by simply letting it *try* to work in any/all of them. the WM/DE in question will need a system tray, of course. link above has a screen shot of gnome's networking applet running flawlessly in LXDE/openbox.

LXDE is actually a DE, not a WM. is ugly by default, but can look quite nice after about 5 minutes of tweaking. it uses OpenBox as the WM. i like it. ergo, the project linked above :D

---

