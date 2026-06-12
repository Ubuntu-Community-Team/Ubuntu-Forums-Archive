---
title: "Openbox wm configuration questions"
date: 2018-02-12
forum: Desktop Environments
---

### Post by swipisnt on 2018-02-12
Hello, I want to use Openbox window manager but I run into some problems. First of all is I using dual monitors setup, question is how to set up Openbox for two monitors? Second question is gnome control center not working on Openbox is there some alternatives to system setting app or maybe should I need use openbox-gnome-session (this session not working for me and want to know how to fix this, at this moment looping back to login screen)?

Thank you in advance!

---

### Post by TheFu on 2018-02-12
openbox uses **obconf** for GUI-level configuration, but most of the power comes from editing an XML file in ~/.config/openbox directly.

Using multiple monitors is an X/Windows thing, so it depends on the GPU and settings for it. For Intel GPUs, I use lxrandr. arandr or xrandr would work equally well, I suppose.  Last time I used nVidia, they had a special nvidia-setup program, but that has been a very long time.

The release of ubuntu you are using can matter since 17.10 changed away from X11 by default.

---

