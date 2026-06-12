---
title: "configure Talika dockbar"
date: 2011-05-13
forum: Desktop Environments
---

### Post by Alfons81 on 2011-05-13
Hi all,

I'm trying Talika on a Xfce. I really like it, but cannot manage to configure it by right click. Might be because I'm running it trough Xfapplet? Anyway is there any way to configure it, any text file...I searched it on ~/.configure but nothing there. As well on internet I couldn't find any solution. 

I know Xfce has an own iconozed dockbar applet, but I guess Talika is more configurable. Or there is any tweak for the inner dockbar applet on Xfce? 

Thanks in advance, cheers!

---

### Post by Pirate Zoro on 2011-07-17
I'm also using xfce with Talika, and figured out how to configure it a bit. First, what you want to do is install gconf-editor. Enter this in a terminal:
```
sudo apt-get install gconf-editor
```
then run it using the command
```
gconf-editor
```
then click thru to /apps/xfapplet/applet_0/prefs (yours might be a different number, depending on whether or not you are running anything else with xfapplet)

There, you can configure things like whether or not to show window previews, system icons, etc.

Hope this helps :D

---

