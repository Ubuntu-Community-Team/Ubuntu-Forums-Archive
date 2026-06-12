---
title: "Wallpaper-tray Problem"
date: 2009-11-08
forum: Desktop Environments
---

### Post by lateralus01 on 2009-11-08
I'm trying to use wallpaper-tray to make my wallpaper alternate like a slideshow every once and a while.  It worked when I installed it from the package manager and then added it to my panel, but I wanted it to switch my wallpaper more often so I changed the time delay from 1 to 0.9.  Well, the thing went crazy switching my wallpaper every half a second and I couldn't get the menu up to change it back so I logged out and back in and it was still switching like crazy although now the icon on the panel is gone so I can't even get to the menu.  I tried uninstalling it completely from the package manager and logging out (that's the only way I can get it to stop) and then reinstalling it, but the second I click the add button to add it to my panel for some reason it remembers the configuration and starts going crazy again so I can't get to the menu to edit my preferences.  Can anyone help me with this?

Thanks,
Lateralus01

---

### Post by peculiar penguin on 2009-11-08
Run
```
gconf-editor &
```Navigate to /apps/wp_tray, set the "n_timeout" key to a sane value, close Configuration editor.
```
killall gnome-panel
``` to make it reload its configuration.

---

### Post by dansi on 2009-11-09
If it doesn't work I would backup your files (dual boot install Linux if you're unable to access them through Vista) and re-install. Or better yet, upgrade to Windows 7 which is coming out soon and runs faster and is better. Or better yet, stick with Linux which is completely free and less prone to Windows malware. Or better yet, get a Mac for the higher chance that everything will work properly.

Are you using a genuine copy of Vista, having properly entered the product key? If not you are simply experiencing the wrath of Microsoft.
===============================
[Self Certification Mortgage UK](http://www.self-cert-mortgage-centre.co.uk/self-certification-mortgage-uk.html)
[Start a home based business](http://www.nitroblueprint.com)

---

