---
title: "gnome shell ceased to be"
date: 2013-04-21
forum: Desktop Environments
---

### Post by nevle on 2013-04-21
hi, i have 12.04 installed on my laptop and after auto shut down due to a flat battery (oops) gnome shell no longer a works. When i log in it appears as gnome desktop (i think) unity also is broken, no 3d effects, hot corner etc just standard gnome. It appears that something in the background is corrupt but i don't know how to go about fixing it. Any advice? thanks

---

### Post by Frogs Hair on 2013-04-21
If you have terminal access Ctrl + Alt + T in Unity  try the following. The Gnome Shell has 3D requirements but, doesn't use Compiz , so I don't know the reason that it's not working. 

Reset Unity:```
unity --reset
```
Reset Compiz if needed:```
sudo gconftool --recursive-unset /apps/compiz-1
```

---

### Post by nevle on 2013-04-22
thanks, but didnt work, error "root visual is nor GL visual" and then "GLX missing on display 0:0"  I reinstalled compiz but no change. I don't want to reinstall the OS , anyone?

---

### Post by Frogs Hair on 2013-04-22
Post some information about you computer & video driver and put it in code  tags using # on the reply tool bar if you still have terminal access .

General ```
lspci -v
```

Graphics card:```
lspci 
```

---

### Post by nevle on 2013-04-28
Hi,i decided to upgrade to 12.10 in the hope that this would fix the problem, upgrade went very smoothly and computer back to normal. I appreciate all the help, thanks.

---

### Post by Frogs Hair on 2013-04-28
Glad it worked out !

---

