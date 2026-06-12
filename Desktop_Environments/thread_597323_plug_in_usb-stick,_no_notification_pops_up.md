---
title: "plug in usb-stick, no notification pops up"
date: 2007-10-30
forum: Desktop Environments
---

### Post by cei on 2007-10-30
Hello everyone,
the "kde media notifier daemon" is supposed to open a window and notify the user what to do with the new media. This doesn't work for USB, but only for CD/DVD. Also in Konqueror at address "media:/" the already available media are only visible after pressing F5 to reload.
As a workaround for the first part I let the usb-stick automatically open in a new window, but when I "safely remove" it, I get the irritating error that unmount was successfull, but eject failed (would be even more irritating if not :). As I found out, eject is called and unmounts the media, but of course fails to eject it. In several Debian forums it is stated, that a new version of a Debian hal package corrects this. But I have already a brand new gutsy gibbon with the newest package of hal.
How can the first two seemingly connected things be remedied and how is the "kde media notifier daemon" to be called if I have to configure udev, hal and d-bus manually?

greets
cei

---

