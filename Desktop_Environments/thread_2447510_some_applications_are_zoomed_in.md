---
title: "some applications are zoomed in"
date: 2020-07-20
forum: Desktop Environments
---

### Post by RikoW on 2020-07-20
Dear all,

I have the issue, that some (so far only third party) applications appear zoomed in with large and kinda fuzzy fonts and icons. So far that concerns only third party apps in this case Onlyoffice Desktop Editor and Zoom. The issue with the Zoom client started today after updating to 5.1. So far I did not manage to unzoom the application windows with any combination of control keys +/-/0 etc.

This is on 20.04 running Budgie, Gnome or Enlightenment DE all showing the same scale behaviour. Ubuntu Budgie runs here on a Dell Lat laptop. At least with Only Office the issue is not visible when the laptop in connected to the multi-monitor setup in my office. Zoom I had no chance to try that out due to Home Office. Uninstalling and reinstalling of the applications did not help either.

I did ask the search engine but nothing came up.

This is really annoying. Any hint / help / work around would be greatly appreciated.

Thanks and cheers, Riko

---

### Post by Frogs Hair on 2020-07-21
I have noticed this with certain icon themes that caused the panel to be so large I couldn't run any applications . How were the apps installed , deb, snap, flatpack?

---

### Post by RikoW on 2020-07-22
I tried already different icon themes, but that does not seem to make a difference. Installation was done with justz .debs.

Thanks!

---

### Post by Frogs Hair on 2020-07-23
I can resize the app window in zoom from the bottom, but the icons are fixed and included with the application. I've not used Office Only , but do currently use FreeOffice and have used WPS via flatpak without seeing that problem.

---

### Post by RikoW on 2020-07-24
Yeah, I can resize the Zoom or OnlyOffice window alright but that does not scale the fonts or the icons.
I did in the meantime find a work-around  to scale down Zoom by using a QT variable in the exec string. I created a custom launcher by copying the system desktop file to my home directory

```
cp /usr/share/applications/Zoom.desktop ~/.local/share/applications/
```

and modifying the exec entry to be 

```
Exec=env QT_SCALE_FACTOR=0.5 /usr/bin/zoom %U
```

That at least works for starting Zoom via this launcher.

Same trick does not work, however, for OnlyOffice. It will do some scaling but just of the window area but not font and icons. Maybe it's not actually a QT app ...

Anyway, Zoom is much more important for me since I have plenty of other Office suits that work just fine :)

Thanks and cheers, Riko

---

