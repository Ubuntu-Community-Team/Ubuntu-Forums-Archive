---
title: "General Lag after update"
date: 2006-09-18
forum: Desktop Environments
---

### Post by bukzor on 2006-09-18
After doing a general update through aptitude, my laptop is very slowwwwww. It takes close to a second for each keystroke to show and ~5 mins for KDE to start. Same issues in console mode. 'top' shows Xorg as top process at 10-50% 9pretty normal). Anyone else having similar issues/ know how to fix it? I would revert to my old versions if I knew what they were, but I'm not sure what all updated...

---

### Post by karamba_kid on 2006-09-18
I apply updates with apt-get and the log for that is /var/log/dpkg.log I would guess updates through aptitude would be in the same spot.. possibly? Once you work your way through the logs you might be able to find the old packages (.debs) in /var/cache/apt/archives

---

### Post by bukzor on 2006-09-18
Ok i think i've solved it. It had nothing to do with the update. There's a setting in KDE laptop manager to throttle the CPU when running on battery power. I always thought this was non-functional, but apparently it only checks for battery/AC when kdm is started, so i was running at 13% cpu. When I checked the throttle setting, it showed 0% throttle, and plugging in the power supply didnt help, but restarting KDE with AC did fix it. Anyone know where I can request to get this applet fixed?

---

