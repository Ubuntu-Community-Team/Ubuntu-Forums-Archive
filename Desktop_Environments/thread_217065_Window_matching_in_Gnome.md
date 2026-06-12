---
title: "Window matching in Gnome?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by theturtlemoves on 2006-07-16
I use Gnome as a desktop environment because I a) like the panel, b) am used to it, c) use a lot of gtk applications, and d) just like it in general. However, there is one thing that has been annoying me, and that is that doing any sort of window matching is hard.

I've tried devilspie, but I think I haven't quite got the hang of the language, because it doesn't really work consistently.

I switched my window manager from metacity to sawfish, but that broke the one qt application I use regularly (amarok), besides which it also didn't play well with the gnome panel.

Has anyone else figured out a simple and effective way to do window matching in Gnome?

---

### Post by PhilipGanchev on 2007-03-19
I don't know what you mean by window matching, but if you are looking for a way to switch to windows by their title, try the Deskbar panel applet.  You can install it using

  sudo apt-get install deskbar-applet

---

### Post by 23meg on 2007-03-19
> Has anyone else figured out a simple and effective way to do window matching in Gnome?

I use Compiz, and the state and winrules plugins do an excellent job, and are simple to configure.

---

### Post by mannheim on 2007-03-19
wmctrl is quite a simple command-line app that can do this. It doesn't have many features, but suits my needs for a few things.

---

### Post by mannheim on 2007-03-19
Yet another possibility is to use kwin as your window-manager, as it works well with gnome and has a lot of window-matching features.

---

