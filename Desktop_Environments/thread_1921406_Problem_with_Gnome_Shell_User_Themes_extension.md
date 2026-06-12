---
title: "Problem with Gnome Shell User Themes extension"
date: 2012-02-06
forum: Desktop Environments
---

### Post by dbbolton on 2012-02-06
When I open **gnome-tweak-tool** and go to the Theme tab, there is an error message next to **Shell theme** that says "Shell user-themes extension not enabled". When I go to the **Extensions** tab, the error message next to **User themes extension** says: "Unknown extension error".

There is no helpful output from the console either:
```

$ gnome-tweak-tool -v -d

DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.background>
DEBUG   : Found desktop file: /usr/share/applications/nautilus.desktop
DEBUG   : User autostart desktop file: /home/dbb/.config/autostart/nautilus-autostart.desktop
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.nautilus.desktop>
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/theme> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/theme> (--long-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/action_double_click_titlebar> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/action_double_click_titlebar> (--long-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/action_middle_click_titlebar> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/action_middle_click_titlebar> (--long-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/action_right_click_titlebar> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/action_right_click_titlebar> (--long-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/focus_mode> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/focus_mode> (--long-docs)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell>
DEBUG   : Shell version: [3, 2, 1]
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.clock>
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.calendar>
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/button_layout> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/button_layout> (--long-docs)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.settings-daemon.plugins.power>
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.interface>
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--short-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--long-docs)
DEBUG   : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--short-docs)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.settings-daemon.plugins.xsettings>
CRITICAL: Unknown extension error
```

How can I debug this issue?

---

### Post by dbbolton on 2012-02-07
I reinstalled gnome-tweak-tool through aptitude, restarted gnome shell and gnome-tweak-tool, and was able to change the theme.

---

