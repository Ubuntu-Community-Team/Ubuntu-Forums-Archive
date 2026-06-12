---
title: "gnome-weather does not start"
date: 2018-10-22
forum: Desktop Environments
---

### Post by gweinstein on 2018-10-22
Does not start from the gnome clock and not from the terminal. Output of error from journalctl in follow mode:

```

Oct 22 11:43:31 sigma org.gnome.Weath[8472]: JS ERROR: TypeError: location is null
                                             WorldContentView<._onLocationAdded@resource:///org/gnome/Weather/Application/js/app/world.js:151:13
                                             wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
                                             WorldContentView<._init@resource:///org/gnome/Weather/Application/js/app/world.js:115:13
                                             wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
                                             MainWindow<._init@resource:///org/gnome/Weather/Application/js/app/window.js:65:27
                                             wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
                                             Application<._createWindow@resource:///org/gnome/Weather/Application/js/app/main.js:159:16
                                             wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
                                             Application<.vfunc_activate@resource:///org/gnome/Weather/Application/js/app/main.js:191:19
                                             wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
                                             main@resource:///org/gnome/Weather/Application/js/app/main.js:207:13
                                             run@resource:///org/gnome/gjs/modules/package.js:225:12
                                             @/usr/share/org.gnome.Weather/org.gnome.Weather.Application:6:1



```

Seems like it requires a location to start but I can't input a location if the widget does not start. Is this like Catch 22? :-)
Thanks for any help and sorry if there is already an answer (I couldn't find any on the forums).

---

### Post by dino99 on 2018-10-22
On which version & DE you get that issue ? Works fine on Bionic/Cosmic with gnome-shell on xorg DE here.

---

### Post by gweinstein on 2018-10-22
Same I think. Output of wmtcrl -m:

Name: GNOME Shell
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

---

### Post by gweinstein on 2018-10-30
Help anyone?

---

### Post by Frogs Hair on 2018-10-30
Is the open weather extension installed and enabled in tweaks > extensions ? I was also able to install gnome-weather, but  had to start from the terminal the first time to get an icon in the dock. Gnome weather from clock is a different extension than open weather.

---

### Post by gweinstein on 2018-11-13
Thanks! Installed and using open-weather extension. Seems to work just fine. Now, how do I remove the "Weather Select Location" from the clock menu. Thanks in advance.

---

### Post by Frogs Hair on 2018-11-13
I'm not clear about what you're asking. Can you upload a screenshot ?

---

### Post by gweinstein on 2018-11-13
[ATTACH=CONFIG]281625[/ATTACH][INDENT][/INDENT]

---

### Post by Frogs Hair on 2018-11-13
I don't see that with open weather. Have you removed/uninstalled all other weather extensions and logged out and in ?

---

### Post by gweinstein on 2018-11-13
It's not part of open weather. It's some other extension, but I don't remember how I installed it and how I turned it on... :-(

---

### Post by Frogs Hair on 2018-11-13
Is it the linked extension ? 

[https://extensions.gnome.org/extension/1380/weather-in-the-clock/](https://extensions.gnome.org/extension/1380/weather-in-the-clock/)

---

### Post by gweinstein on 2018-11-13
OK done. I just removed gnome-weather. duh!

Thanks for the help!!

---

