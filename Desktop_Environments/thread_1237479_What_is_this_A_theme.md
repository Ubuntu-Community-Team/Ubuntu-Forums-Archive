---
title: "What is this? A theme?"
date: 2009-08-11
forum: Desktop Environments
---

### Post by low_mat on 2009-08-11
Ubuntu has booted into this a few times. I'm running 9.04 64 bit. My friend said he gets this if he uses VNC. I don't get any error messageand I haven't done anything different to my system. At first I though it was a safe-mode type environments but I have full functionality. If I reboot it does away. Any help?

[IMG]http://img81.imageshack.us/img81/6997/screenshot1fzl.png

How it normally looks:
[IMG]http://img256.imageshack.us/img256/6259/screenshotclc.png

---

### Post by rainwalker on 2009-08-11
Something with your themes has gone wrong, but I'm not sure what. If you run "gnome-settings-daemon" in a terminal, do you get any errors or messages?

---

### Post by RedSingularity on 2009-08-11
Yeah that is another theme.  Cant you change it and reboot?

---

### Post by rainwalker on 2009-08-11
> **Shadow121 said:**
> Yeah that is another theme.  Cant you change it and reboot?

It's not really a theme, it's the lack of one

---

### Post by RedSingularity on 2009-08-11
> **rainwalker said:**
> It's not really a theme, it's the lack of one


Oh yeah......i didnt even think of that.  So then why not install one quickly?

---

### Post by rainwalker on 2009-08-11
> **Shadow121 said:**
> Oh yeah......i didnt even think of that.  So then why not install one quickly?

That might work, but I doubt it; things usually end up looking like that when something isn't found that Ubuntu is looking for with the theme. For example, after a fresh install, if you install any new themes by dragging-and-dropping in the Appearance window, it won't install for administrative applications and they end up looking exactly like that (blocky and blue). You have to create some symbolic links so that administrative apps know that you installed themes in a different directory than it is looking for.

---

### Post by low_mat on 2009-08-12
> **rainwalker said:**
> It's not really a theme, it's the lack of one

That's what this other guy told me. I went ahead and installed a custom theme. I'll see if it does it again. If not problem solved then.

---

### Post by gjoellee on 2009-08-12
This usually happens when you install a theme that requires a gtk engine that you not installed. Could you post the output of ```
gnome-settings-daemon
``` so we may help you further?

---

### Post by low_mat on 2009-08-12
It happened before I had even messed with any themes. Here's the output.

```
matt@brown:~$ gnome-settings-daemon

** (gnome-settings-daemon:8666): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:8666): WARNING **: Could not acquire name

```

---

