---
title: "Conky apps key binding so that no need to minimize the windows open to see desktop"
date: 2011-03-27
forum: Desktop Environments
---

### Post by jao_madn on 2011-03-27
Hi 

I would like to ask if someone try or is there any key binding about the  conky apps..I would like to know if it possible to key bind the conky  running in desktop so that everytime i want to see the running conkyrc  on the desktop there is no need for me to minimize the open windows  inorder just to see my running information in the desktop

Thanks in advance

---

### Post by stinkeye on 2011-03-28
**[COLOR="Red"]Edit[/COLOR]** This only seems to work with compiz.
**Edit2** It will work when running metacity if you remove the **below** option in **own_window_hints**.

Use wmctrl to toggle your conky window above,below.
Install wmctrl...
```
sudo apt-get install wmctrl
```


Give your conky window a title by editing your conky config.
Add...
```
own_window_title myconky
```


Also check other settings are the same as mine
especially **own_window_type normal**
eg my settings
```
own_window yes
own_window_type normal
own_window_title myconky
own_window_hints undecorated,below,skip_taskbar,skip_pager
```


Create a custom keybind in keyboard shortcuts (or add a panel launcher) using
```
wmctrl -a myconky -b toggle,above
```
in the command box.

---

