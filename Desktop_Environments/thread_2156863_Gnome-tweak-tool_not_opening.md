---
title: "Gnome-tweak-tool not opening"
date: 2013-06-23
forum: Desktop Environments
---

### Post by dansofe0r on 2013-06-23
Hello everyone. I'm having problems with the gnome-tweak-tool. When I installed it today it was able to enable a bunch of extensions from the extensions website. Then when I tried to open the GUI interface of the program it wouldn't open. When trying to open from the terminal I got 

$ gnome-tweak-tool 
(gnome-tweak-tool:2233): GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.user-theme' is not installed
Trace/breakpoint trap (core dumped)

The peculiar thing is that I had tried uninstalling earlier followed by removing the extras repositories in sources.list. After re installing the tool opened correctly but after switching enable user themes extension on, and doing alt+f2 and entering r, the tool would not open again after being closed and produce the same error message when trying to open it from the terminal. 

Is there a way to fix this issue? I'd appreciate any help!

---

### Post by dino99 on 2013-06-23
the issue is from "user themes" (had not worked lastly)

---

