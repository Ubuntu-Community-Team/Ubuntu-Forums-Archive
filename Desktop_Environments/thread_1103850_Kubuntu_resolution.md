---
title: "Kubuntu resolution"
date: 2009-03-23
forum: Desktop Environments
---

### Post by toypilot on 2009-03-23
Hi All

I just installed Kubuntu over 8.04 and when it starts the resolution is so small and fonts so BIG that I can't do anything. It wont let me change the resolution because I can't get to the bottom of the window to adjust the settings. Any ideas how I can change the resolution via config file or something rather than using the user interface?

In Gnome its running at 1024 which is coming from the config file in X11..

Any help appreciated.

tp

---

### Post by toypilot on 2009-03-23
Update, 

Accessing the systemsettings via terminal provided scroll bars which allowed me to edit the resolution. Although this changes the resolution the fonts are still enormous, preventing me from doing much with the system

Anyone resolved this issue?

Thanks

tp

---

### Post by Marlonsm on 2009-03-23
You can try dragging the window, even without using the window titlebar.
I think the default for it is Alt+left click anywhere in the window.

---

### Post by izizzle on 2009-03-23
Boot into a terminal environment and tyoe the following to upgrade your system.

```
sudo apt-get update
sudo apt-get upgrade
```

---

