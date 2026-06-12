---
title: "[SOLVED] killall pulseaudio on boot"
date: 2008-12-11
forum: General Help
---

### Post by zika on 2008-12-11
I want to kill(all) pulseaudio when computer boots. I do not want (yet) to uninstall it. I have tried to put a line ```
killall pulseaudio
``` in /etc/rc.local but that did not do the trick. After boot pulseaudio is alive and well till I do $killall pulseaudio. I tried to put a line ```
sh -c "sleep 10 && killall pulseaudio"
``` but with the same effect. Any help will be greatly appreciated.

---

### Post by kostkon on 2008-12-11
> **zika said:**
> I want to kill(all) pulseaudio when computer boots. I do not want (yet) to uninstall it. I have tried to put a line ```
killall pulseaudio
``` in /etc/rc.local but that did not do the trick. After boot pulseaudio is alive and well till I do $killall pulseaudio. I tried to put a line ```
sh -c "sleep 10 && killall pulseaudio"
``` but with the same effect. Any help will be greatly appreciated.
Check if you can find it in *System &#8594; Preferences &#8594; Sessions*.

---

### Post by jocko on 2008-12-11
Pulseaudio is not loaded during boot, it's loaded as part of the gnome session. Just inactivate it in the gnome-session-properties (System-->Preferences-->Sessions)...

---

### Post by zika on 2008-12-11
> **jocko said:**
> Pulseaudio is not loaded during boot, it's loaded as part of the gnome session. Just inactivate it in the gnome-session-properties (System-->Preferences-->Sessions)...

No, that does not work. Even when I inactivated that in Sessions it still was showing sleeping in a process list. Sessions were the place where I've put a new item with ```
pkill pulseaudio
``` or even better ```
pulseaudio --kill
``` and that did the trick.

I've tried lots of places (blacklisted it in /etc/modprobe.d/blacklist ... a line in /etc/rc.local killing it ... changing attributes in /etc/init.d/ for pulseaudio (removing x-'s) (a sugestion from a good friend of mine) ...) and nothing did the trick.

But, now its gone from the process list and I am not unprepared for a distribution update (what uninstalling it might have done)

Thanks. Marking it [SOLVED] and I'm moving to another challenge ...

---

