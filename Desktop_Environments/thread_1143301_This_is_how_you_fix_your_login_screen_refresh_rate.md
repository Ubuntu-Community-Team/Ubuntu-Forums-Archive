---
title: "This is how you fix your login screen refresh rate and/or resolution"
date: 2009-04-29
forum: Desktop Environments
---

### Post by drawsmcgraw on 2009-04-29
Using Ubuntu Jaunty.

After reading [this document]("https://wiki.ubuntu.com/X/Config/Resolution") I found out about:

```
 xrandr 
```You need to plunk an xrandr command in one of your startup scripts in /etc/gdm. I chose 

```
/etc/gdm/Init/Default
```I needed to lower my refresh rate because I got that obnoxious "input not supported" floaty box of doom on my login screen. To change it, I just put this line at the top of the file:

```
xrandr -r 75
```There's also --mode if you want to specify a resolution. If you want to learn more, just:

```
man xrandr
```Then hit / on your keyboard and search for your item of interest.

Enjoy!

---

