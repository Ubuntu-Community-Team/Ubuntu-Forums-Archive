---
title: "classic, usb stick shown on desktop?"
date: 2012-05-17
forum: Desktop Environments
---

### Post by ottosykora on 2012-05-17
Earlier with previous versions, when I inserted an usb stick , an icon was displayed on the desktop and could also be ejected from there.

What would be the setting in the current 12.04 and classic desktop?

(on the unity, usb dev are shown as extra icons when mounted)

---

### Post by ajgreeny on 2012-05-27
> **ottosykora said:**
> Earlier with previous versions, when I inserted an usb stick , an icon was displayed on the desktop and could also be ejected from there.

What would be the setting in the current 12.04 and classic desktop?

(on the unity, usb dev are shown as extra icons when mounted)
Just found this and here is the answer.
```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```will work in classic desktop of 12.04, but I've no idea about unity as I don't use it.

---

### Post by kansasnoob on 2012-05-27
> **ottosykora said:**
> Earlier with previous versions, when I inserted an usb stick , an icon was displayed on the desktop and could also be ejected from there.

What would be the setting in the current 12.04 and classic desktop?

(on the unity, usb dev are shown as extra icons when mounted)

In deed, in Unity the mounted volume appears in the Launcher (left side bar), but if you're using classic it appears no where. You might find some useful info here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

More specifically in regards to your question look at step #10 in that thread :)

---

