---
title: "Applying gtk theme to login screen"
date: 2010-01-23
forum: Desktop Environments
---

### Post by akand074 on 2010-01-23
Hello guys,
I recently installed a new theme for my desktop but now my login screen looks like windows 98 lol. I couldn't figure out how to apply my gtk theme to the login screen. I also tried installing a new theme just for the login screen and found a couple alright ones but I can't figure out how to install them. I get places directing me to System > Administration > Login Window or to use GDM but they aren't there and I haven't managed to find out what to install to get them to show up. If I could get a hand installing a new theme or applying my gtk theme to the login screen, either one would be very helpful. 
Thank you very much!

---

### Post by sisco311 on 2010-01-23
try this python script: [thread=1358026]GDM2 Configuration Tool[/thread]

or

run the theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```
or set the theme in gconf editor:
```
sudo -u gdm dbus-launch gconf-editor
```
edit the value of the /desktop/gnome/interface/gtk_theme key

---

