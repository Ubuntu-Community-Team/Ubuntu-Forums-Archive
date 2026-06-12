---
title: "Keyboard layout switcher in Lubuntu"
date: 2013-02-21
forum: Desktop Environments
---

### Post by uzumakifahim on 2013-02-21
I am using LXDE on Ubuntu 12.04. It's pretty easy to configure keyboard layout in Unity, but I'm facing problem when I'm using LXDE. There is an applet for the LXDE panel as "Keyboard layout switcher". I've enabled that, it is only showing US keyboard. Even in the settings window for that applet **there is no option for changing the layout other than english. Not only that, I'm not getting any options to select keyboard shortcut for switching the layouts.**

I know LXDE is a great DE for lightweight desktop. I am really interested LXDE as my default DE. That's why I need to solve this issues.

Please help LXDE gurus!!! Thanks in advance.

---

### Post by TheFu on 2013-02-21
> **uzumakifahim said:**
>  configure keyboard layout 

It is not a GUI app, but a console app.
```
$ sudo dpkg-reconfigure console-setup
```

---

### Post by Rex Bouwense on 2013-02-21
See here:
[http://lxlinux.com/#17](http://lxlinux.com/#17)

---

### Post by uzumakifahim on 2013-03-08
From the discussion it's clear that there is no GUI for changing keyboard layout, but finally I've solved this problem in a different way. I used Ibus for using keyboard layout other than English.

So I'm marking this post as SOLVED!

---

