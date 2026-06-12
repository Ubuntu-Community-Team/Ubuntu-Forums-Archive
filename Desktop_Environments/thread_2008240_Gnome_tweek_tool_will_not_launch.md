---
title: "Gnome tweek tool will not launch"
date: 2012-06-22
forum: Desktop Environments
---

### Post by linuxsam777 on 2012-06-22
I have recently installed cinnamon to ubuntu 12.04 however cinnamon automatically installed light version of gnome-shell. The problem was when I try to change the theme using Gnome Tweak Tool which or some reason would not open. then after that I install the full gnome-shell and still the same problem persists. Has this got anything to do with cinnamon. If so how do you get gnome-tweek-tool to work? It works in Unity.

---

### Post by cortman on 2012-06-22
> **linuxsam777 said:**
> I have recently installed cinnamon to ubuntu 12.04 however cinnamon automatically installed light version of gnome-shell. The problem was when I try to change the theme using Gnome Tweak Tool which or some reason would not open. then after that I install the full gnome-shell and still the same problem persists. Has this got anything to do with cinnamon. If so how do you get gnome-tweek-tool to work? It works in Unity.

Run gnome-tweak-tool from the terminal, and post back whatever errors result in the terminal.

---

### Post by linuxsam777 on 2012-06-22
This is the error I got
```
samuel@robby~$ gnome-tweak-tool  (gnome-tweak-tool:2334): GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.user-theme' is not installed  Trace/breakpoint trap (core dumped)
```
However I that gave me a spark of intelligence because I tried to install user themes from the gnome extensions website but it must have not installed properly

To solve the problem I delete the any user themes folders from .local/share/gnome-shell/extensions

Then I reinstalled user themes with the terminal by typing
```

sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions

```

Thanks for the help!!!

---

### Post by hakermania on 2012-06-22
> **linuxsam777 said:**
> This is the error I got
```
samuel@robby~$ gnome-tweak-tool  (gnome-tweak-tool:2334): GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.user-theme' is not installed  Trace/breakpoint trap (core dumped)
```
However I that gave me a spark of intelligence because I tried to install user themes from the gnome extensions website but it must have not installed properly

To solve the problem I delete the any user themes folders from .local/share/gnome-shell/extensions

Then I reinstalled user themes with the terminal by typing
```

sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions

```

Thanks for the help!!!
Mark the thread as solved, please :)

---

