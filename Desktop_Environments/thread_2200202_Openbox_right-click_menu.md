---
title: "Openbox right-click menu"
date: 2014-01-18
forum: Desktop Environments
---

### Post by vasa1 on 2014-01-18
I'm getting to like the Openbox right-click menu which displays what is specified in **menu.xml**. By default, this menu is displayed by right-clicking on an exposed area of the desktop.

I'm wondering if it's possible to display the menu by pressing a couple of keys. In other words, I'd like to assign, say, the super key plus the spacebar (in **rc.xml**) to bring up the menu without needing to find a blank space on the desktop to right-click on. Any thoughts on whether that's possible?

---

### Post by vasa1 on 2014-01-18
I found this: [https://wiki.archlinux.org/index.php/Openbox#Menus](https://wiki.archlinux.org/index.php/Openbox#Menus) :)
> Desktop Menu

It is also possible to create a keybind to access the desktop menu. For example, the following code will bring up the menu by pressing CTRL + m:

```
<keybind key="C-m">
    <action name="ShowMenu">
       <menu>root-menu</menu>
    </action>
</keybind>

```

And it works. I'm using "W-space" instead of "C-m".

---

### Post by vasa1 on 2014-01-18
Continuing with the "keyboard only" way to use the "right-click" menu, pressing the first letter of the "label" will launch that item or, if there's more than one item with the same first letter, pressing that letter will cycle through these items.

Another way is to use "shift+underline" *before* the letter one wants to assign as the "accelerator". So if I want to launch ObConf by pressing "b", I'd have "O_bConf" as the label in menu.xml instead of plain ObConf but when the menu is opened I'll see O_b_Conf and know that I can press "b" to launch ObConf.

---

### Post by vasa1 on 2014-01-20
If you want to right-click menu to always appear in a fixed spot on your screen and if you have **xdotool** installed ...

Edit the <keyboard> section of *rc.xml to include
```
    <keybind key="C-m">
      <action name="execute">
        <command>right-click-menu</command>
      </action>
    </keybind>

```
Have this executable script called "right-click-menu" in your path:
```
#!/usr/bin/env bash

xdotool mousemove 20 5
sleep 0.2
xdotool click 3

```
Reconfigure Openbox and now the right-click menu will always open 20 px to the right of the top left corner and 5 px down.

Edit (20140122): the mousemove x and y values should indicate an area of your desktop you know will **always** be unoccupied by an application.

On my system, I needed to have "sleep 0.2" [to make things work]("http://unix.stackexchange.com/q/110092/15760"). Maybe better systems won't need the sleep. IDK.

---

