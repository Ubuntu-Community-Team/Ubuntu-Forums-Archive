---
title: "Get rid of yellow outline when opening apps"
date: 2006-07-26
forum: Desktop Environments
---

### Post by saracen on 2006-07-26
I have compiz/XGL working and with all the effects its redundant to also have that ugly yellow outline box that shows up when you open an application from the panel.  Does anyone know how to get rid of it?

---

### Post by saracen on 2006-07-27
anyone?

---

### Post by tturrisi on 2006-07-27
[http://www.ubuntuforums.org/showthread.php?t=211062](http://www.ubuntuforums.org/showthread.php?t=211062)

---

### Post by saracen on 2006-07-27
wicked... thanks!

---

### Post by saracen on 2006-07-27
I jumped the gun... the problem persists.  I'm using XGL/Compiz - so no metacity.  Making the changes in gconf hasn't had any effect... are there any other suggestions?

---

### Post by Anduu on 2006-07-28
The key you are looking for is under /desktop/gnome/interface/enable_animations

Uncheck it...

You may want to reenable the reduced rescources key in case you go back to regular gnome...you'll be wondering why window contents don't show when you move a window...

---

### Post by mcduck on 2006-07-28
You could also try disabling apps/panel/global/enable_animations (if I remeber the key correct). This is how I disabled those animations altough some people claim that it doesn't work for them :confused:

---

### Post by saracen on 2006-07-28
yup, it was the apps->panel->global->enable_animations key.  Thanks.

---

