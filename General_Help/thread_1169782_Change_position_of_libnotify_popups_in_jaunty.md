---
title: "Change position of libnotify popups in jaunty"
date: 2009-05-25
forum: General Help
---

### Post by dan000 on 2009-05-25
Libnotify popups appear in the top right corner of the screen. This is a problem for me, as I have a non-rectangular desktop (TwinView dual monitor setup with different resolutions on the monitors), and the popups are appearing off the screen.

I could change the layout so that the right monitor is top-right, instead of bottom-right, but this is not ideal because of the physical layout of the monitors.

So, I tried to find a way to change the position of the popups so that I would actually see them. I found some reference to a gconf setting, but I wasn't able to find that. I can't find any other way to change the position of the popups. Is there anything I can do?

---

### Post by super.rad on 2009-05-25
Are you sure it's libnotify and not the new notify-osd (the ones in the picture)

[IMG]https://wiki.ubuntu.com/NotifyOSD?action=AttachFile&do=get&target=notification-bubble.jpg[/IMG]
If it is libnotify there should be something about popup settings in System > Preferences.
If it's notfify-osd then theres no way to change the position of them

---

### Post by dan000 on 2009-05-26
> **super.rad said:**
> Are you sure it's libnotify and not the new notify-osd

Yes, it's notify-osd, which uses libnotify. That's why the pidgin-libnotify plugin is required for pidgin to send notifications to it.
It's not notification-daemon, which was the old one before notify-osd, which must be what you're talking about.

Maybe I should uninstall notify-osd, and install notification-daemon.

---

### Post by dan000 on 2009-05-26
> **dan000 said:**
> Maybe I should uninstall notify-osd, and install notification-daemon.

Well, I installed notification-daemon, but didn't uninstall notify-osd, because ubuntu-desktop depends on it (why?).

I can't figure out why in the world Ubuntu switched to notify-osd now. notification-daemon is more configurable, and the standard theme (not the default ubuntu theme) I think is actually more attractive than the notify-osd popups.

The only problem now is to figure out how to get notification-daemon to start instead of notify-osd when I log in.

---

