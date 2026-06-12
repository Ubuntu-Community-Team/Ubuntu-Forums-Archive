---
title: "Replace standard notification icons with smaller ones"
date: 2011-03-07
forum: Desktop Environments
---

### Post by Gonik on 2011-03-07
Hello there! Some hours ago i finally decided to remove Windows 7 from my netbook and install Ubuntu. Although i have *some* experience with Linux, i never sat down to customize the looks of it.

So after i tried both Desktop & Netbook editions, i liked the Desktop better. Not to mention the Netbook edition loaded the menus slower than GNOME itself.

I deleted the top panel and in the bottom one i kept only the stuff i needed:
[LIST]
[*]Main Menu (it reminds me of the start menu, plus it's more compact from the Custom one)
[*]Window List
[*]Notification Area (where the Wifi icon appears)
[*]Indicator Applet (X11 lang indicator, Battery info, Volume & Mail)
[*]Drawer (with the avaliable Workspaces)
[*]Indicator Applet Session (Username & Shut down/restart/suspend button)
[/LIST]

The thing is, as it is the Indicator Applet takes up quite some space on a small netbook screen. Is it possible to use smaller icons for e.g. the X11 indicator. It's not necessary to display the Keyboard icon and 3 letters of the language name.
Maybe it can display only the 2 letters of the lang. (e.g. US)? Or even to display a *small* country flag?

Also another question i'd like to answer. I've noticed that some applications (like Skype) put their icon in Notification Area, while Transmission put it in Indicator Applet. Why is that? Is it some different kind of notification method?

Thank you in advance for any attention you may pay to my questions. :D

---

### Post by Krytarik on 2011-03-07
Generally it's not possible (in most cases) to specify the size of the items, you can only choose to remove them at all. Personally I have removed "indicator-me" (username, status), "indicator-sound" and the Network Manager (I have a fixed line internet connection).

These are the items and how to remove:

indicator-me: remove package
indicator-sound: remove package
indicator-messages: remove from panel
Network Manager: disable in "System -> Preferences -> Startup Applications"
indicator-session: remove from panel
keyboard-layout-indicator: may not work in 10.10, enter in a terminal
```
gconftool-2 -s /desktop/gnome/peripherals/keyboard/general/disable_indicator -t bool true
```To show "flags" instead of letters in the keyboard-layout-indicator: enter in a terminal
```
gconftool-2 -s /desktop/gnome/peripherals/keyboard/indicator/showFlags -t bool true
```But however, I don't get "real" flags then.

Greetings.

---

### Post by Gonik on 2011-03-09
Thanx for your time Krytarik! not exactly wht i had in mind, but you certanily pointed me to the right direction for searching! :)

---

