---
title: "Accurate Window Positioning With Geometry"
date: 2013-05-09
forum: Desktop Environments
---

### Post by CosmicFlux on 2013-05-09
Hi,

I've created a custom desktop session in Lubuntu 13.04. When I log in to the session I have two terminal windows and an instance of xclock running. Once I positioned the windows in the way I want them to appear on login I ran the **xwininfo** command to gather the geometry values. I've written a bash script specifying the size and geometry of the windows and their position on the screen. but when I log in the positioning is messed up with windows overlapping and I have to manually move them back into position.

Any suggestions?


Cosmic

---

### Post by vasa1 on 2013-05-09
> **CosmicFlux said:**
> ... I've written a bash script ...

Any suggestions?

1: Could you share the contents of the script?
2: Have you considered positioning windows using the **applications** section of *~/.config/openbox/lubuntu-rc.xml*?
3: I wouldn't know about how to specify two windows of the same application :(

---

### Post by CosmicFlux on 2013-05-09
```
#!/usr/bin/env bash

xsetroot -solid "#000000" &

metacity &

gnome-terminal --geometry 108x47+24-5 --hide-menubar

xclock -digital -update 1 -bg "#000000" -fg "#ffffff" -fn -*-*-bold-*-*-*-16-*-*-*-*-*-*-* -padding 6  -geometry 285x25-13+16 &

exec gnome-terminal --window  --title=+Status+Main-Menu --hide-menubar --geometry 43x43-19-7
```

---

### Post by vasa1 on 2013-05-09
> **CosmicFlux said:**
> ```
...metacity ...
```
Okay, so calling it Lubuntu confused me. If you're using another window manager, lubuntu-rc.xml isn't useful.

---

### Post by CosmicFlux on 2013-05-11
Sorry, I should have been more clear in my post. Yes, I'm specifying the use of Metacity in the bash script. 

Here is a screenshot of the session I've created. I would like to have it presented like this upon login. 

[http://imageshack.us/photo/my-images/24/screenshotfrom201305120.png/]("http://imageshack.us/photo/my-images/24/screenshotfrom201305120.png/")

Cosmic

---

### Post by CosmicFlux on 2013-05-12
Problem solved! I figured out a solution. 

Thanks for your assistance. 


Cosmic

---

