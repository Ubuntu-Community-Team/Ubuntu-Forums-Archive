---
title: "Keyboard Problem"
date: 2006-02-05
forum: Desktop Environments
---

### Post by sacoskun on 2006-02-05
Hi,

I have installed Ubuntu 5.10 and I have set my keyboard layout to Turkish. Nonetheless, when I press Turkish letters from the keyboard they do not appear on the screen and also I cannot use AltGr key in order to make (backslash) or (at sign).

How can I solve this problem,

Kind Regards,

Sarp Arda Coskun

---

### Post by sacoskun on 2006-02-05
I also do not have /etc/X11/ can this be the problem?
I cannot also change any other keyboard layouts, I got error.

Kind Regards,
Sarp

---

### Post by dcstar on 2006-02-05
[QUOTE=sacoskun]I also do not have /etc/X11/ can this be the problem?
I cannot also change any other keyboard layouts, I got error.

Kind Regards,
Sarp[/QUOTE]
Exactly what "error"?

---

### Post by sacoskun on 2006-02-05
An error window pop-up exactly like;

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Kind Regards,
Sarp

---

### Post by sacoskun on 2006-02-05
Thank you to Saul Perdomo had sent its answer, you can find it from [http://ubuntuforums.org/showthread.php?t=75052&page=2&highlight=altGr+key](http://ubuntuforums.org/showthread.php?t=75052&page=2&highlight=altGr+key)

---

