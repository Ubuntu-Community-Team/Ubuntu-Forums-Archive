---
title: "How to give an applet in the panel Sudo privileges?"
date: 2007-05-28
forum: Desktop Environments
---

### Post by noxxle on 2007-05-28
I want to give the ** xfce4-cpu-freq-plugin** applet for Xubuntu sudo privileges so that I can change my power governor by clicking on it. You can do this in Gnome by using the "sudo dpkg-reconfigure gnome-applets" command. Obviously, this won't work in Xubuntu. How can I do this? 

This plugin is in Feisty's repos, you can find more info here:

[http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin)

---

### Post by aysiu on 2007-05-28
```
gksudo xfce4-cpu-freq-plugin
``` should work.

---

### Post by noxxle on 2007-05-29
dobbbob@dobb:~$ gksudo xfce4-cpu-freq-plugin
xfce4-cpu-freq-plugin: command not found
dobbbob@dobb:~$


Its not a command, its an applet that runs in the panel. I want to give it permanent sudo permissions.

---

### Post by noxxle on 2007-05-31
buemp

---

### Post by noxxle on 2007-06-08
moooooooooo

---

