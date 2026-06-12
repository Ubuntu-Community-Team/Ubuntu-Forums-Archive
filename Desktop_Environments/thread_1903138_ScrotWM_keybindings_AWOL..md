---
title: "ScrotWM keybindings AWOL."
date: 2012-01-01
forum: Desktop Environments
---

### Post by casbahdk on 2012-01-01
I have been trying to get ScrotWM to work with Lubuntu, but there is no response to any keys when I log-in. I have also installed suckless-tools, so I should be able to open programs including PCManFM, quit ScrotWM, etc. but nothing happens when I use the commands either with ctrl, alt, or the win key. I have tried this on my desktop computer, on a laptop, in VirtualBox OSE, etc. The results are the same -no response to anything. What is going on? Can anyone shed any light on this? I have done the following before I logged out of Openbox and into ScrotWM:```
cp /etc/scrotwm.conf $HOME/.scrotwm.conf 
```

---

### Post by Rodney9 on 2012-01-01
Scrot's default key setting in Lubuntu 11.10 is the print screen key.

Key Bindings are set in -
```
/home/user/.config/openbox/lubuntu-rc.xml
```


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

