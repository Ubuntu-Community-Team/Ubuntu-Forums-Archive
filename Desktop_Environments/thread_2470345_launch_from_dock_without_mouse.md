---
title: "launch from dock without mouse"
date: 2021-12-27
forum: Desktop Environments
---

### Post by dwater on 2021-12-27
Hi,

Some time ago, the dock on ubuntu (not sure what desktop, but the default one) had a feature where it showed a little number on each icon and you could use the keyboard shortcut - Window+number - to launch the app.

I see that I can still do that, but I have to know the number beforehand - previously, it would show me the number when I press the Window key and the dock would pop out.

Any idea how to get the previous behaviour?

Max.

---

### Post by vanadium on 2021-12-27
You can change the dock to display the number overlay with the command
```

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-overlay true

```

---

### Post by dwater on 2021-12-27
That didn't seem to work (even after fixing the typo 'doc' -> 'dock')...however, searching on that gsettings key got me what I wanted:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1861310](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1861310)

well, 'super + q' which is good enough :D Actually, that only works after '[COLOR=#000000][FONT=&quot]gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-overlay true' so it isn't quite how I remember - which is they would be shown on the dock all the time....but, yeah, good enough, thanks :D

[/FONT][/COLOR]Max.

---

