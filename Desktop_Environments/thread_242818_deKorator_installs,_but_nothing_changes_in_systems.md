---
title: "deKorator installs, but nothing changes in systemsettings/kcontrol"
date: 2006-08-24
forum: Desktop Environments
---

### Post by ZiZi on 2006-08-24
I decided to use deKorator to have all the settings in one place. The installation went fine, no error messages, however, it doesn't seem to affect the systemsettings/kcontrol in an appropriate way.

When I start systemsettings/kcontrol and open Appearance -> Window decorations, there are the same two tabs - window decoration and buttons - and nothing else, no additional tabs as suggested in some dekorator screenshots.

Also, it takes considerably more time to load the Window decorations sections, sort of a short hang-up occurs. If launched from konsole, systemsettings produce this output: ```
adding Colors /usr/share/applications/kde/colors.desktop
adding Fonts /usr/share/applications/kde/fonts.desktop
ScimInputContextPlugin()
adding GTK styles and fonts /usr/share/applications/kcmgtk-xdg.desktop
systemsettings: WARNING: KLocale: trying to look up "" in catalog. Fix the program
adding Icons /usr/share/applications/kde/icons.desktop
adding kbfx Applet /usr/share/applications/kde/kcmkbfx.desktop
kdecore (KConfigDialogManager): WARNING: A widget named 'kcfg_ThemeList' was found but there is no setting named 'ThemeList'
kdecore (KConfigDialogManager): WARNING: A widget named 'kcfg_CategoryWidth_2' was found but there is no setting named 'CategoryWidth_2'
adding Style /usr/share/applications/kde/style.desktop
adding Window Decorations /usr/share/applications/kde/kwindecoration.desktop
```

According to this [KDE-Look.org dekorator thread]("http://www.kde-look.org/content/show.php?content=31447"), there are supposed to be some configuration files in ~/.kde/share/config/ and ~/.kde/share/apps/ entries created, but none had actually been. It also seems like one of the forum users has got the same issues.

Any ideas what could have gone wrong?

---

### Post by Jucato on 2006-08-24
I could only try to answer the first one:
You have to select deKorator from the drop-down list first, before any changes could take effect. Immediately below the "Window Decoration" tab name, there's a drop-down list of installed window decorations. choose deKorator from there, and you will have your additional tabs.

---

