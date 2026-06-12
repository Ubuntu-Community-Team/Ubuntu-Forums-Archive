---
title: "Notification position"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Gustavo Daniel on 2010-04-30
How can i fix the position of the notification? I want more in the top.

[IMG]http://farm5.static.flickr.com/4026/4566449443_33b0958a62_o_d.png[/IMG]

---

### Post by 3rdalbum on 2010-04-30
To "fix" something implies that it's broken, which it isn't. The notifications are there by design. However, you can change the location of the notifications to a certain extent. This Launchpad answers page tells you how: [https://answers.launchpad.net/notify-osd/+question/80515](https://answers.launchpad.net/notify-osd/+question/80515)

---

### Post by ztrange on 2010-05-13
I'm sorry but I cant find any useful information in that link. Is there a way to revert the notify-osd positioning behavior to the one used in karmic?

Thanks

---

### Post by icyrainz on 2010-05-13
I'm having the same issue. Usually, the first notification appears on the top then the next one stacks down. But now it skips the first slot and directly appear in the second slot :(
Any way to revert to default setting ?
I tried to use the notification-daemon but it did not work and now I cannot remove it at all, it asked me to remove all the notification plugins of other apps.

---

### Post by payonk on 2010-05-13
It's not a bug it's a feature :)
Just like the the close button on the left side of window, it's really useful when you close window every time when you try to access menu's

---

### Post by europa on 2010-05-18
[http://files.myopera.com/freejerk/files/bug-feature.jpg](http://files.myopera.com/freejerk/files/bug-feature.jpg)

---

### Post by stinkeye on 2010-05-19
If you really want to change the position use this tutorial which uses a patched version of Notify OSD.
[**_[COLOR="DarkRed"]Customize Notify OSD Notification Bubbles[/COLOR]_**]("http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html")

and there is now a [**_[COLOR="#8b0000"]GUI To Configure NotifyOSD In Ubuntu[/COLOR]_**]("http://www.webupd8.org/2010/05/gui-to-configure-notifyosd-in-ubuntu.html")

You can change a number of settings
Typical Notify OSD config
```
slot-allocation = fixed
bubble-expire-timeout = 10sec
bubble-vertical-gap = 5px
bubble-horizontal-gap = 5px
bubble-corner-radius = 37,5%
bubble-icon-size = 30px
bubble-gauge-size = 6px
bubble-width = 240px
bubble-background-color = 131313
bubble-background-opacity = 90%
text-margin-size = 10px
text-title-size = 100%
text-title-weight = bold
text-title-color = ffffff
text-title-opacity = 100%
text-body-size = 90%
text-body-weight = normal
text-body-color = eaeaea
text-body-opacity = 100%
text-shadow-opacity = 100%
```

---

