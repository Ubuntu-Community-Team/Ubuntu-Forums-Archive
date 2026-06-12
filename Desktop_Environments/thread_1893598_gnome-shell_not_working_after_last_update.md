---
title: "gnome-shell not working after last update"
date: 2011-12-10
forum: Desktop Environments
---

### Post by choel on 2011-12-10
After an update 3 days ago gnome-shell stopped working, trying to restart it with ```
gnome-shell --replace
``` only results in another crash and the keyboard stops working.

This is what I get when trying to start gnome-shell: ```
st_widget_get_theme_node called on the widget [0x24112a0 StButton.status-chooser-user-icon] which is not in the stage.
``` and ```
gnome-shell-calendar-server[4829]: Got HUP on stdin - exiting Trace/breakpoint trap
```

If I look in the xorg.0.log I got this error:```
 gnome-session[5321]: WARNING: App 'gnome-shell.desktop' respawning too quickly
``` and ```
: CRITICAL: We failed, but the fail whale is dead. Sorry....
```

Ran "metacity --replace" just to get the window borders back for now. The interesting thing is if I log in to xfce I got the same problem, no window boarders, must run "metacity --replace" in xfce also.

Running Ubuntu 11.10 with gnome-shell 3.2.1.

---

### Post by plaw on 2011-12-10
The problem is caused by the gnome-shell Alternative Status Menu extension:
[https://bugzilla.redhat.com/show_bug.cgi?id=739271](https://bugzilla.redhat.com/show_bug.cgi?id=739271)

You can try the workarounds suggested in the previous link, or read here for how to remove the extension:

[https://wiki.archlinux.org/index.php/GNOME#When_an_extension_breaks_GNOME](https://wiki.archlinux.org/index.php/GNOME#When_an_extension_breaks_GNOME)

---

### Post by lolpenguin on 2011-12-10
> **plaw said:**
> The problem is caused by the gnome-shell Alternative Status Menu extension:
[https://bugzilla.redhat.com/show_bug.cgi?id=739271](https://bugzilla.redhat.com/show_bug.cgi?id=739271)

You can try the workarounds suggested in the previous link, or read here for how to remove the extension:

[https://wiki.archlinux.org/index.php/GNOME#When_an_extension_breaks_GNOME](https://wiki.archlinux.org/index.php/GNOME#When_an_extension_breaks_GNOME)

Umm...not really. Any extension can cause GNOME Shell to break. Delete the extension/uninstall it. Extensions are located in /usr/share/gnome-shell/extensions/ OR ~/.local/share/gnome-shell/extensions.
EDIT: [email]system-monitor@paradoxxx.zero.gmail.com[/email] broke the Shell after upgrade to 3.2.1.

---

### Post by vanlong441 on 2011-12-11
> **lolpenguin said:**
> Umm...not really. Any extension can cause GNOME Shell to break. Delete the extension/uninstall it. Extensions are located in /usr/share/gnome-shell/extensions/ OR ~/.local/share/gnome-shell/extensions.
EDIT: [EMAIL="system-monitor@paradoxxx.zero.gmail.com"]system-monitor@paradoxxx.zero.gmail.com[/EMAIL] broke the Shell after upgrade to 3.2.1.

to add to lolpenguin,
extensions and shell themes do break the shell. If it is broken, we can ctrl alt backspace to log out and log into the fallback mode. Then from there follow lolpenguin's instruction.

---

