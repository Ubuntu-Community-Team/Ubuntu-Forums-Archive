---
title: "Changing tray icons"
date: 2013-08-11
forum: Desktop Environments
---

### Post by converted on 2013-08-11
I'm making a more serious stab at using KDE4 than I have in the past, so I'm not really sure how things *should* work in some cases.

Case in point - I have changed through a few different icon themes, and none of them seem to change the tray icons.  Is this handled separately from the rest of the system icons somehow?

This is a nearly fresh install of Kubuntu 13.04 - various tweaks in the week since I installed it, but nothing crazy...

I'd really like to get rid of those gradient-laden monochrome tray icons and go to something flatter (dare I say it - more like the default Ubuntu tray icons) - it's actually nearly my last visual complaint.  But I can't seem to change them *at all*.

Being that this is KDE, I'd be surprised if this is something that requires me to do it manually, but darn if I can figure it out.

Can someone point me in the right direction?

Thanks!

Edit:  I'm talking about the standard indicators, Klipper, Network Status, Volume, etc...)

---

### Post by bra|10n on 2013-08-17
System tray icons are set as part of KDE's plasma theming; 
~/.kde4/share/apps/desktoptheme/

That said, if you've changed to a plasma theme that _does not_ contain it's own icons then KDE will continue to use the default oxygen set.

_Edit:_ If you wanted to use a different icon set you would simply put them in the ~/.kde4/share/apps/desktoptheme/you_preferred_theme/icons

---

