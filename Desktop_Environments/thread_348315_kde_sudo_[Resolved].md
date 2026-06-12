---
title: "kde sudo? [Resolved]"
date: 2007-01-28
forum: Desktop Environments
---

### Post by PlancksCnst on 2007-01-28
Is there a way to sudo an app without using a terminal?  I would like to not have to open a terminal and do sudo kate [filename] and then leave it open every time I need to edit a file like xorg.conf. Typing sudo etc doesn't seem to work from run dialog.

---

### Post by taurus on 2007-01-28
<Alt>F2 -> kdesu kate filename

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by thelocust on 2007-01-28
[B]
You can get a service menu added for Konqueror called [Edit as Root]("http://kde-apps.org/content/show.php?content=11998"). Also I have a Run Command box in my panel, Its a applet thats basicly a little terminal box that you can quickly type commands in to. Also you should use kdesu instead of sudo this will get you the little root password box that pops up when you open Adept.



[/B]

---

### Post by PlancksCnst on 2007-01-28
Thanks - that kdesu is exactly what I was looking for!

---

### Post by TheWizzard on 2007-01-28
kate is a very nice editor. however, it can be useful to learn terminal-based editors like nano. 

```
sudo nano -B /etc/X11/xorg.conf
```

---

### Post by PlancksCnst on 2007-01-28
Thanks - I usually use vim when I use a text mode editor.  On a file like xorg.conf, however, I like to be able to quickly scan it.  A scrollbar comes in nicely for that, as I can fix my eyes on a part of the screen and scrub the bar back and forth.

---

