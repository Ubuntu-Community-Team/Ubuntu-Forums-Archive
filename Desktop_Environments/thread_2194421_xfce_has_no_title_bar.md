---
title: "xfce has no title bar"
date: 2013-12-18
forum: Desktop Environments
---

### Post by deanie44 on 2013-12-18
I recently did a fresh install of Mythbuntu on a partition on my Dell PC.  Everything was perfect until I install Ubuntu Desktop Environment from Ubuntu Control Centre.  Ubuntu install correctly, but I am missing the tile bar or navigation bar for xfce.  I have tried [COLOR=#333333][FONT=Helvetica Neue]xfwm4 --replace in a terminal and nothing is restored. I need some guidance.  Any help will be appreciated.  sister5091

[/FONT][/COLOR]nadine@nadine:~$ xfwm4
xfwm4-Message: To replace the current window manager, try "--replace"


(xfwm4:3159): xfwm4-WARNING **: Another Window Manager is already running
nadine@nadine:~$

---

### Post by Frogs Hair on 2013-12-18
Navigate to settings Window Manager and try another theme if the command fails to work.  Next, logging out and back in to xfce.

---

### Post by deanie44 on 2013-12-18
Hi Frogs Hair.  I tried your suggestion, but it did not work.  Any more suggestions?  Thank you.  sister5091

---

### Post by Frogs Hair on 2013-12-18
I came across this command on a solved forums thread for a similar problem. 

```
xfwm4 --replace --daemon
```

---

