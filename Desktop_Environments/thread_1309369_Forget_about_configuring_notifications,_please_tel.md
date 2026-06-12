---
title: "Forget about configuring notifications, please tell me how to kill it"
date: 2009-11-01
forum: Desktop Environments
---

### Post by zubaran on 2009-11-01
Sory for posting again. But How to switch off this darn notifications? I removed Indicator-applet, indicator-applet-session, but I still get info what track is playing or what messages come in pidgin...

---

### Post by zubaran on 2009-11-03
I add some info in case someone could benefit from it, but for the first time I switched to Fedora from Ubuntu to avoid nervous experience.
It appears that there is no way to remove this notify-osd system in 9.10.
To suppress it however you can install gnome-stracciatella-session. 
[https://wiki.ubuntu.com/DesktopTeam/Specs/Jaunty/StracciatellaSession](https://wiki.ubuntu.com/DesktopTeam/Specs/Jaunty/StracciatellaSession)

To disable it only in Pidgin use
Tools -> Plugins and untick Libnotify Popups

Long live notifiy-osd! But I get off immediately.:evil:

---

### Post by terazen on 2009-11-03
This is how I did it on my laptop a few minutes ago and it seemed to do it.

```
sudo chmod -x /usr/lib/notify-osd/notify-osd 
```

---

