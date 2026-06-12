---
title: "how to undo problems caused by nvidia-settings"
date: 2007-10-15
forum: Desktop Environments
---

### Post by dugh on 2007-10-15
I have a dell d820 laptop with nvidia 7400 card.  Everything has worked perfectly fine.  I am using gutsy now.

I tried nvidia-settings (trying to get a projector display working better) and it completely messed up my machine.

I think it changed to another nvidia driver (gfx/glx?) or something, it may have enabled xinerama, I can't tell.
xorg.conf seems to be the same as before.  I restored a backup copy of xorg.conf and the problems still remain.

When I login I get an error message about display settings not working, then I can only login at 640x480 mode.

I tried the 'screens and graphics' control panel but it doesn't show my nvidia card.  I tried similar nvidia models and the nv model but none fixed the problem.

How can I undo whatever nvidia-settings does to your machine?

---

### Post by Crooksey on 2007-10-15
Do you have the file...

```

/etc/X11/xorg.conf.backup
```

If so try using that, nvidia-settings should make a backup file when saving changes.

---

### Post by dugh on 2007-10-15
I restored the backup earlier and it made no difference.

Apparently nvidia-settings changes the display driver on its own.

I had to completely remove nvidia-settings, and then reinstall nvidia-glx-new (which you can also do by unchecking and rechecking the nvidia driver in the restricted drivers control panel).
That plus restoring xorg.conf fixed the issue.

---

### Post by Crooksey on 2007-10-15
Post the xorg.conf?

---

