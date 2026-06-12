---
title: "mouse cursor size"
date: 2012-02-27
forum: Desktop Environments
---

### Post by TheRacerX on 2012-02-27
does anyone know how to change the mouse cursor size in Ubuntu 11.10, like a simple way not some overly complicated thing cause i don't want to go through the process of changing 2 million different settings to do it 

thank you

---

### Post by musicman10489 on 2012-02-29
I don't know if this is more complex than what you are looking for but you can install 
```
dconf-tools
```
then in your terminal run
```
$ dconf-editor
```
then navigate to org -> gnome -> desktop -> interface

Here you should be able to change your cursor size and theme. I hope this was helpful!

---

