---
title: "Different images for the different virtual desktops"
date: 2014-05-21
forum: Desktop Environments
---

### Post by donstonesucks on 2014-05-21
i now there are probably hundreds of these posts, but ive checked several that said they were solved to see if they worked for me.  unfortunatly they did not,  i would like to know how to set different images for each virtual desktop.  ive checked this: [http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace](http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace) , but it didnt work because my compiz didnt have wallpaper in its filter.  i also checked the alternitve on that page that said to use dconf-editor, but once again, no options under the dropdown for wallpaper.

I am currently running Ubuntu 14.04

---

### Post by deadflowr on 2014-05-21
```
sudo apt-get install compiz-plugins
```
if on 14.04
```
sudo apt-get install compiz-plugins-extra
```
if on 12.04.

It should add wallpaper to ccsm.
(I think)

---

### Post by donstonesucks on 2014-05-21
> **deadflowr said:**
> ```
sudo apt-get install compiz-plugins
```
if on 14.04
```
sudo apt-get install compiz-plugins-extra
```
if on 12.04.

It should add wallpaper to ccsm.
(I think)

thanks that made it show up in compiz.

---

