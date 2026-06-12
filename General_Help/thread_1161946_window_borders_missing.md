---
title: "window borders missing"
date: 2009-05-17
forum: General Help
---

### Post by ivanvajar on 2009-05-17
At one point this day, my system went back to login window. I had to repair Xserver, reconfigure mu graphics card and detect monitor again. Everything is OK now, but window borders are missing in GNOME. Any idea what's to do?

---

### Post by VCoolio on 2009-05-17
First look if you have visual effects enabled and in compiz (if you use that) the window decoration plugin. Also see if running <gtk-window-decorator> in the terminal gives any errors (post them here). And try <metacity --replace> .
If the problem persists, try if a new created user (system > admin > users and groups, create new and login there) has the same problem. If not, then it's a problem in your user config settings. You can delete (or rename) /home/you/.gconf and login again. The folder will be created again with default settings.
If a new user has the same problem, it's in your system and I wish you all the best and a happy new year. I have the same in Jaunty and also had it in Intrepid. It seems an incredibly difficult thing to keep working. I recommend installing emerald and using an emerald window border theme. 
If you have a NVidea card you can try adding the following lines to /etc/X11/xorg.conf (in Section Device), it's a solution to a bug that may also be my problem but it doesn't work for me:
```
	Option	"AddARGBVisuals" "True"
	Option	"AddARGBGLXVisuals" "True"
```

---

### Post by fajerpeter on 2009-05-24
Same problem but found solution on the Forums (unfortunately cannot find the original link).     
a) reinstall compiz
b) install compiz fusion icon
c) in the startup programs add:   compiz-fusion
d) logout and in

good luck

---

### Post by ivanvajar on 2009-07-09
fajerpeter, I saw your post just now and this was the solution. However, problem was my RAM. RAM failed at one point and messed things up. Not just Compiz, but a lot of things went bad. It's all OK now and fajerpeter, thank you.

---

### Post by nuchdog on 2011-03-02
try this. 

[http://www.ubun2.com/question/329/why_ubuntu_window_title_bar_missing]("http://www.ubun2.com/question/329/why_ubuntu_window_title_bar_missing")

run
metacity --replace

---

