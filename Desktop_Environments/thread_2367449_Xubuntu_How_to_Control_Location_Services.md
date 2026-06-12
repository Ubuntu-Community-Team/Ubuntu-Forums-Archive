---
title: "Xubuntu: How to Control Location Services?"
date: 2017-07-30
forum: Desktop Environments
---

### Post by themeadows94 on 2017-07-30
I'm running Xubuntu 16.04. I just installed gnome-weather, and it automatically determined my location. In Gnome, I can switch off these services. How do I switch off location services in Xubuntu? Who provides location services?

Really unsettling from a privacy perspective that this would be enabled automatically on a Linux distro. One of the major reasons I use Linux as much as possible is cos it enables a level of privacy impossible with Windows/Mac

---

### Post by vasa1 on 2017-07-30
Well, mainline linux distros are made for the general public. If you have specific needs, you need to attend to them yourself either by finding out how to turn off automatic location detection or by using privacy-oriented distros.

You could go through [https://www.wilderssecurity.com/threads/escaping-from-geolocation-awareness-in-linux.382961/](https://www.wilderssecurity.com/threads/escaping-from-geolocation-awareness-in-linux.382961/) for some pointers.

---

### Post by again? on 2017-08-01
> **themeadows94 said:**
> I'm running Xubuntu 16.04. I just installed gnome-weather, and it automatically determined my location. In Gnome, I can switch off these services. How do I switch off location services in Xubuntu? Who provides location services?

Really unsettling from a privacy perspective that this would be enabled automatically on a Linux distro. One of the major reasons I use Linux as much as possible is cos it enables a level of privacy impossible with Windows/Mac
gnome-weather, gnome-clocks and gnome-maps install as a dependency geoclue-2.0.
geoclue-2.0 is a default install in Gnome but access needs to be enabled by the user in Privacy Settings.

You could install dconf-editor.
```
sudo apt install dconf-editor
```
and navigate to **/org/gnome/system/location/**
where you can deny apps access to location information.
**TIP:** dconf-editor is easier to navigate when used unmaximized.

---

