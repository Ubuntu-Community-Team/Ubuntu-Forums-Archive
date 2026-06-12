---
title: "Installing XGL and Compiz altered my keyboard"
date: 2006-09-03
forum: Desktop Environments
---

### Post by gynther on 2006-09-03
I installed XGL and Compiz following the [thread posted by poofyhairguy]("http://www.ubuntuforums.org/showthread.php?t=131267") and the installatin went without a hitch. However, it seems as though my keyboard layout has gone from my cozy swedish to something else. My Alt Gr key doesn\t work and neither does my traditional swedish only letters. 

I have all the swedish language packs installed that I can find and my Gnome is in swedish. I cant however find any relevant keyboard settings. Can anyone tell me where too look or what to do to get my swedish layout back? I searched the forum but couldnt find any posts about this.

---

### Post by _simon_ on 2006-09-03
Did you do this bit?

> 
Read the rest of this paragraph then reboot. After login in GDM, open a terminal and enter this (credit to rjtd):
```

Code:
xmodmap /usr/share/xmodmap/xmodmap.<language>

```
replacing you country code for language. For US English I use this command:
```

Code:
xmodmap /usr/share/xmodmap/xmodmap.us

```


I believe se is swedish? 

so: 
```

xmodmap /usr/share/xmodmap/xmodmap.se

```

---

### Post by gynther on 2006-09-03
Thanks! That fixed it! I need to open my eyes...

---

### Post by fettuohi on 2006-11-06
I have the same problem with my danish keyboard on Kubuntu 6.10 Edgy. I'm running Beryl instead of Compiz my keyboard layout is also changed by XGL, so that my Alt Gr button doesn't work. I have tried the fix, but I get an error

gd1331@andre:~$ xmodmap /usr/share/xmodmap/xmodmap.dk
xmodmap:  unable to open file '/usr/share/xmodmap/xmodmap.dk' for reading
xmodmap:  1 error encountered, aborting.

What I usually do and this works is setting

gd1331@andre:~$ setxkbmap -model pc105 -layout dk -variant basic
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'

but I don't where to put this line in so that when my KDE/XGL start this command is issued. Any help?

Regards

André

---

### Post by fettuohi on 2006-11-10
Anybody got a solution?

Regards

André

---

### Post by didobuntu on 2006-11-10
xmodmap.dk does not resolve the problem under Kubuntu. This only fixes it under gnome and maybe also under xfce.

For kubuntu look at [this]("http://ubuntuforums.org/showthread.php?t=291518&highlight=Alt+Gr") topic.

---

