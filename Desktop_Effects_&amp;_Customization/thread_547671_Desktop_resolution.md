---
title: "Desktop resolution"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by hojjat on 2007-09-10
I have set my screen resolution to 1024*768, but only affects after I login. The login screen itself is still shown at 800*600. I need a way to fix it. I read [this thread]("http://ubuntuforums.org/showthread.php?t=487878") but it didn't help. What do you suggest?

---

### Post by Chymera on 2007-09-12
you need to reconfigure your x server, close x and then run 
```
sudo dpkg-reconfigure xserver-xorg
```
It's kind of self-explanatory.

---

### Post by hojjat on 2007-09-14
Great, just how do I close X and run a command?

Oh, and it asks some question (like about the graphic card, etc) How do I know the correct answers?

PS:I'm going to test [Startup Manager]("http://www.getdeb.net/app.php?name=Startup+Manager") too.

---

### Post by smartboyathome on 2007-09-14
You can close X and run a terminal by doing control+alt+f1.

---

### Post by Chymera on 2007-09-15
no, that just makes it go into the background. To stop it run
```
sudo /etc/init.d/gdm stop
```

and the same thing only with start at the end, in order to start it

---

