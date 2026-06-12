---
title: "gdms, splashes, themes.. confused.."
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by m0n on 2007-06-19
Hi guys!
I'm quite new to Ubuntu so sorry for maybe stupid questions..
I have Feisty installed with Gnome environment and the other day decided to change look and feel.  I came across gnome-look.org, that is where confuse started :)

This site has a lot of sections, my understanding is following:
1. Icon themes - is what you can find under System --> preferences --> Theme 
This makes different set of Icons, border colors, buttons etc...
2. GDM Themes - is what you can install under System --> Administration --> Login Window --> Local tab
This is to change Login screen, its' background etc..
3. Splash screens   - is under System --> preferences --> Splash Screens
This is the image you get right after log in..
4. GTK 2.x - Could you please clarify on this? What are these sets..? how to install?
5. Compiz - This is some windows manager, you should install and then you can use those themes for it.. 
This makes all windows look different etc...
Is it right??
6. Metacity - This is another windows manager and as I understood it comes with ubuntu by default? Right?

Now how Compiz and Metacity work with each other? should one be uninstalled before use of another?
If compiz is installed does it interfere with Themes/splash screens/etc??
Or are all this "sections" are changing different parts of look and feel, and to achieve full customization of all parts of the Gnome these should be installed?
I'm lost :)
Thanks in advance!

---

### Post by Warbo on 2007-06-19
Hi, it does seem a bit confusing doesn't it? I, like many others, think there should be general themes which apply to everything, but since that has not been implemented yet I'll try to clear up the confusion:
GTK is the GIMP ToolKit (so GTK 2 is the latest version), it is the library which is used by all GNOME programs to draw their buttons, scrollbars, menus, etc. GTK themes can be installed and used through the System>Preferences>Theme tool. That tool handles GTK 2 themes, GNOME icon themes and Metacity themes. (Note that KDE, the desktop system used by Kubuntu and available through the package manager, doesn't use GTK, but uses a different library called QT. If you want to customise QT programs then you need the 'kcontrol' package from System>Administration>Synaptic Package Manager. Note that QT themes can be given custom colours, so the only thing you should be looking for on sites like kde-look.org is the shape of the buttons)

Compiz draws the titlebars on windows (if you have it enabled), and also the thin border around their edges. I am not too sure on how to install Compiz themes sorry (I prefer Beryl, which likes to use "Emerald" themes, but can also use Metacity ones).

Metacity is the default window manager, so you will probably be using this to draw your window titlebars and borders. Metacity themes can be installed with System>Preferences>Theme.

Clicking on te Customize button in the theme tool lets you mix and match icon, GTK and Metacity themes. This is also useful if a theme doesn't specify a complete look, after installing it might only appear in the lists inside Customize and not in the main theme list.

Hope that helps :)
Warbo

Edit: Compiz, Metacity, Beryl, etc. can all be installed at the same time and won't conflict. However, only one can be run at a time, so whenever you start up one of them then the previous one will be stopped. If you are using Beryl (which I prefer to Compiz) then the beryl-manager package makes switching between them nice and easy. Otherwise, Compiz can be enabled/disabled with System>Preferences>Desktop Effects, and if you are not using either of those then you shouldn't really have to worry about it.

Also, the gnome-splashscreen-manager package makes changing your GNOME splash screen easier

---

### Post by LT1Caprice57L on 2007-09-05
I don't seem to see a Splash Screens option in my System --> Preferences menu.  I, too, am running Feisty.

EDIT:  JUST KIDDING...A qiuck trip to Synaptic Package Manager fixed the problem :)

Me = n00b. ;)

---

