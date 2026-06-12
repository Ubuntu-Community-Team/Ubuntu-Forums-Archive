---
title: "Firefox doesn't launch from menu"
date: 2012-11-22
forum: Desktop Environments
---

### Post by dkarnows on 2012-11-22
Since upgrading to Xubuntu 12.10 Firefox doesn't launch from the menu or from a launcher on my Xubuntu panel. No GUI error message is displayed and the process continues running in the background, but no window opens. Firefox does however launch fine when I open a terminal and run it from the command like. When I modify the menu/panel launch item so that the stdout/stderr is redirected I get these errors which I don't get when I run it from the command line:

```

(firefox:2822): GLib-GObject-WARNING **: cannot register existing type `GdkWindow'

(firefox:2822): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(firefox:2822): Gdk-CRITICAL **: gdk_window_get_display: assertion `GDK_IS_WINDOW (window)' failed

```

Any help appreciated.

---

### Post by rai4shu2 on 2012-11-23
What's the setting in Settings Manager / Preferred Applications for "Web Browser"? It sounds to me like that didn't get upgraded properly.

---

### Post by dentaku65 on 2012-11-23
What about to launch from terminal:

```
LIBGL_ALWAYS_SOFTWARE=1 firefox
```

---

### Post by dkarnows on 2012-11-23
> **rai4shu2 said:**
> What's the setting in Settings Manager / Preferred Applications for "Web Browser"? It sounds to me like that didn't get upgraded properly.

It was "Debian Sensible Browser". I changed it to "Mozilla Firefox" & rebooted. No better. Still can't launch from menu/panel.

> **dentaku65 said:**
> What about to launch from terminal:

```
LIBGL_ALWAYS_SOFTWARE=1 firefox
```

Launches fine from the terminal when I do this. But as stated in the original post it always worked fine when I launch from the terminal (with or without that LIBGL_ALWAYS_SOFTWARE=1). My problem isn't launching from a terminal. My problem is launching directly from the Xubuntu menu ("Internet -> Firefox Web Browser") or panel (both of which are just set to launch "firefox").

---

### Post by dentaku65 on 2012-11-24
Sorry I've read incorrectly your #1 post; how your firefox launcher from panel looks?

Here is mine.

---

### Post by dkarnows on 2012-11-24
> **dentaku65 said:**
> how your firefox launcher from panel looks?


Mine is identical to yours.

---

### Post by dentaku65 on 2012-11-24
> **dkarnows said:**
> Mine is identical to yours.

Are you using the default Xubuntu Greybird theme?

---

### Post by dkarnows on 2012-11-26
> **dentaku65 said:**
> Are you using the default Xubuntu Greybird theme?

I wasn't. I don't think I was running any theme (nothing was highlighted). I changed to Greybird and tried again. No luck. Still no window when launched from menu or panel. I've since changed to the Clearlooks theme (which also doesn't fix my problem, but looks nice ;-) )

---

### Post by bonzodog on 2012-12-01
I am also getting this frankly strange behaviour. Anyone got any ideas? Like OP, just installed Xubuntu ontop of ubuntu 12.10.

Edit: solved this after another 10 minutes of fiddling. Try editing the launcher entries to include the whole path, so it launches with /usr/bin/firefox. This works.

---

### Post by dkarnows on 2012-12-03
> **bonzodog said:**
> Edit: solved this after another 10 minutes of fiddling. Try editing the launcher entries to include the whole path, so it launches with /usr/bin/firefox. This works.

Doesn't work for me. I think my problem must be different from yours.

---

