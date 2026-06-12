---
title: "Ubuntu 16.04.3 LTS gnome-session-fallback metacity, nautilus border"
date: 2017-08-27
forum: Desktop Environments
---

### Post by jerryferry on 2017-08-27
Ubuntu 16.04.3 LTS gnome-session-fallback metacity, nvidia driver 375.66, desktop intel computer.


I have a problem with nautilus having no visible borders on the right hand side and the bottom. Overlapping nautilus windows can be hard to tell apart along these edges.


Searches have only yielded  information from older ubuntu versions.

---

### Post by Perfect Storm on 2017-08-27
Have you tried switching GTK theme?

---

### Post by jerryferry on 2017-08-27
Only 3 themes in system settings/ appearance. Ambiance(default), Radiance, High Contrast. In the past have switched between Ambiance and Radiance to toggle attempted edits in the themes folder. These changes made no difference so restored back from a copy. Just tried High Contrast, got an ubuntu internal error & lost HP, from the try. Will reboot & hope that was temporary.

---

### Post by jerryferry on 2017-08-27
Rebooted, Hp, back in tray, printed test page, seems ok. Some time back I did make the following change that made it possible to resize certain windows which resisted resizing, Catfish was one of the problem windows.

gksu gedit  ~/.config/gtk-3.0/gtk.css 
.window-frame {
    margin: 10px;
}

---

### Post by Perfect Storm on 2017-08-27
Try a theme which are darker, I suggest you try: [https://github.com/horst3180/arc-theme](https://github.com/horst3180/arc-theme)
It may be compiled first or try the ppa for it (I had no luck with it, but you might): [https://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme](https://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme)

Here's how it looks: [https://github.com/horst3180/arc-theme/blob/master/README.md](https://github.com/horst3180/arc-theme/blob/master/README.md)

---

