---
title: "Autostart entry keeps reverting"
date: 2021-03-10
forum: Desktop Environments
---

### Post by Regexaurus on 2021-03-10
I'm running the Rise Vision (digital signage) media player on Lubuntu 20.04.2 LTS w/ LXQt. The Rise Vision install script creates an Autostart entry (corresponding file appears at ~/.config/autostart/rvplayer.desktop). The Rise Vision Autostart entry doesn't work as expected, by default. The media player doesn't launch upon login. In the rvplayer.desktop file is a line:

```
Exec=bash -c '/home/risevision/rvplayer/scripts/start.sh --unattended'
```

With the help of [Tomáš Peitl's comment on this Unix.StackExchange post]("https://unix.stackexchange.com/questions/449116/why-does-lxqt-autostart-not-do-anything#comment1183746_449278"), I found if I remove "bash -c'" and the trailing single quote, so that line is instead:

```
Exec=/home/risevision/rvplayer/scripts/start.sh --unattended
```

save my changes and reboot, the Rise Vision media player automatically launches, as desired. Unfortunately, the change doesn't persist. The Exec line won't revert immediately after reboot and login. I can reboot a number of times without the line reverting, but eventually (same day) the Exec line is changed back to the original, non-working line that calls bash. I suspect the trouble might be with the Rise Vision media player, or perhaps a media player update script, but thought I would start here. Does LXQt, SSDM, and/or Lubuntu do something that would cause this line to revert, as described, and if so, how can I prevent it? I've considered changing permissions on the file, but haven't yet tried/tested that. Oh, I also changed that setting through the LXQt Session Settings gui dialog, in case modifying rvplayer.desktop directly would cause the described problem. That made no difference.

Thank you!

---

### Post by Regexaurus on 2021-03-10
~/.config/autostart/rvplayer.desktop was user-writable (755) by default. It appears that unsetting the write bit (chmod 555 rvplayer.desktop) might be a workaround. I would still like to learn whether it's something system related (LXQt, SDDM, XDG, etc.) or a Rise Vision process (player, updater) that was setting it back. I'm guessing the latter.

---

### Post by CatKiller on 2021-03-10
> **nomencl8ure said:**
> I would still like to learn whether it's something system related (LXQt, SDDM, XDG, etc.) or a Rise Vision process (player, updater) that was setting it back. I'm guessing the latter.

It will be the latter. The 'bash -c' is an anti-pattern, and that software is set up to habitually change its own files from the cloud. You could get in touch with them and tell them to stop doing it, but I couldn't say that they'd listen.

---

