---
title: "GTK 2.x Themes and 'Ubuntulooks' engine"
date: 2006-09-24
forum: Desktop Environments
---

### Post by cmost on 2006-09-24
I searched these forums buy couldn't find any references to this problem.  I'm having a problem with random applications not taking on the look of themes which use the 'Ubuntulooks' engine.  The native 'Human' theme works perfectly with these same applications, but when I install other themes which supposedly use the same engine, such as:

Forwardlooks:
[http://www.gnome-look.org/content/show.php?content=46192](http://www.gnome-look.org/content/show.php?content=46192)

Or, Human-Blue
[http://www.gnome-look.org/content/show.php?content=36396](http://www.gnome-look.org/content/show.php?content=36396)

certain applications fail to pick up the theme and instead use an ugly GTK 1.x looking theme (see screenshots of Synaptic using Human versus Forwardlooks themes.)  I've installed the above packages by draging them onto the theme applet and then selecting them from the list.  Can anyone explain how I can configure the themes to ensure that they are used by all applications?  Thanks!

---

### Post by simon360 on 2006-09-24
Hey

You need to extract the contents to /usr/share/themes, your problem is that the themes in question are only installed for you. When you use an application as root, the theme can't be accessed. 

Hehehe, I feel really special, I made Forwardlooks... :D lol

simon360

---

### Post by ayoli on 2006-09-24
or link ~/.themes to /root with 
```
sudo ln -s /home/user_name/.themes /root
```

---

### Post by cmost on 2006-09-24
Thanks guys!  I figured it must be something odd like that!  Simon360, I love your theme right now since I hate Ubuntu's default oranges and browns!  Pretty please make one with blue scroll bars?

---

### Post by ocdude on 2006-09-24
Wow, I've been wondering for a long time why any apps run as root didn't use my theme...thanks!

---

