---
title: "GNOME keyboard error message on login (gnome-settings-daemon)"
date: 2008-04-03
forum: Desktop Environments
---

### Post by saibatizoku on 2008-04-03
Hi to everyone!

I'm having an annoying problem with GNOME everytime that I login to my MacBook (1st Gen) having to do with the keyboard.

This is the message that I get right after login:

```

Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/media
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/calculator
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/search
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/email
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/help
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/www
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/play
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/stop
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/previous
Type mismatch: Expected `string' got `float' for key /apps/gnome_settings_daemon/keybindings/next

```


I've already tried using **gconf-editor**, both as a regular user and with sudo, and I've actually been able to unset some of these keys, but the settings are not saved when I login next time.

I would greatly appreciate any guidance with this.

Asides from a few issues of this sort, I'm happy to say that I'm running Ubuntu 7.10 ***without*** Dual Boot on the MacBook, and it's better than fantastic!

---

