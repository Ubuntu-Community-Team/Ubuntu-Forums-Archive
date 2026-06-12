---
title: "lose panel icons"
date: 2010-12-26
forum: Desktop Environments
---

### Post by emilemma on 2010-12-26
i create several icons on the bottom panel; all are for web sites using firefox- (firefox [www.yahoo.com](www.yahoo.com)) for instance. i lock them to panel & all is ok until the system is restarted. then all or some of the icons are missing... this is intermittent in nature...
i am completely puzzeled... any ideas??
i am new to ubuntu & linux in general.. 

thanks

---

### Post by karthick87 on 2010-12-26
To reset the gnome panel to defaults, type this in a terminal,
```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

### Post by emilemma on 2010-12-26
if i do this, will i lose all my panels, icons & etc. from my desktop??

thanks :)

---

### Post by emilemma on 2010-12-26
i just tried the gconftool command & nothing happened??:(

P. S. this only occurs on the bottom panel.. all icons on top panel are not effected????

---

### Post by Bobhuber on 2010-12-27
> **emilemma said:**
> i create several icons on the bottom panel; all are for web sites using firefox- (firefox [www.yahoo.com]("http://www.yahoo.com")) for instance. i lock them to panel & all is ok until the system is restarted. then all or some of the icons are missing... this is intermittent in nature...
i am completely puzzeled... any ideas??
i am new to ubuntu & linux in general.. 

thanks
Heres what worked for me. Edit the applications menu on the top panel and create the shortcut  there under one of the menu items wherever you want. Then right click on the bottom panel > add to panel > application launcher and select the shortcut (launcher) you created above.

---

