---
title: "help with IceWM and gnome-screensaver in Ubuntu Lucid"
date: 2010-07-31
forum: Desktop Environments
---

### Post by erfahren on 2010-07-31
I haven't been able to find a solution to this...

I'm running an IceWm session in Ubuntu 10.04 and have a startup script in ~/.icewm with the following:
```

gnome-settings-daemon &
gnome-screensaver &
gnome-power-manager &
gnome-volume-manager &
(sleep 5; nm-applet --sm-disable&) &
(sleep 10; parcellite&) &

```
my screensaver won't come on, nor will my computer go into standby (but works in Ubuntu) - my display does go to sleep after 20min, however

I'm not sure what I'm missing. I'm starting to get the impression that the information I've come across about this is outdated.

Do I need to start something else as well? I think I could install xscreensaver but I'm not sure how that would affect Ubuntu and I'd mostly prefer that the standby worked.

any suggestions? thanks

edit: oh - this is on an older Dell 2400 desktop with an Nvidia video card, not the laptop listed in my sig (if that matters)

---

