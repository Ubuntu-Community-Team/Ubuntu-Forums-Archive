---
title: "Always on top Keyboard shortcut (compiz)"
date: 2010-06-01
forum: Desktop Environments
---

### Post by geoffm on 2010-06-01
I normally have a keyboard shortcut to toggle Always-on-top, that I setup using gconf. Since I started using compiz instead of metacity, the shortcut doesn't work anymore. I couldn't find where we can define one in compiz.

It's useless to tell me I can just do Alt-Space, T . I want to be able to toggle really quickly without having to hunt down a menu item. I don't even use the keyboard shortcut really, I use mouse gestures with easystroke and the shortcut is just there to allow me to do the command.

---

### Post by zzanzare on 2010-06-14
I would like to have this "Always on top" shortcut as well.. I have been using Alt+A previously, but it used to be in Compiz Config under the "Extra WM Actions" plugin. Now in Lucid Lynx this plugin is not there, and I cannot find the option to set it up anywhere else. Is it possible to set it up for example in gconf-editor?

---

### Post by stinkeye on 2010-06-14
I have **extra wm actions** on my lucid install, in CCSM under Window Management.
According to the compiz wiki, extra wm actions is in the compiz-fusion-plugins-main package.

Another way to have a toggle above command is to use wmctrl.
```
sudo apt-get install wmctrl
```



And add a keyboard shortcut using ```
wmctrl -r :ACTIVE: -b toggle,above
```as the command.



> **geoffm said:**
>  I use mouse gestures with easystroke and the shortcut is just there to allow me to do the command.
You could also assign the same command to a mouse gesture using **easystroke**

There's a couple of other wmctrl commands I use with easystroke that you 
may find useful in this post... [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8444754&postcount=5[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=8444754&postcount=5")

---

### Post by hype on 2011-05-01
thanks for this tip ! Emerald being unusable (so i couldnt add a "always on top" button to my window border), it's a nice way to do without having to right-click on a window border to be able to have it stuck on top...

---

