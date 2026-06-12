---
title: "Replacing compiz with metacity"
date: 2007-10-31
forum: Desktop Environments
---

### Post by zlosynus on 2007-10-31
Hi,

I just uninstalled all packages containing compiz and also xserver-xgl. But after restarting there were no layouts for windows.

I can run metacity manualy by command:
```
metacity --replace display-0
```
And then everything works fine. How can I make it automaticly after logging??

---

### Post by k0rfain on 2007-10-31
why didnt you just disable the desktop effects completly? :P

---

### Post by Thyme on 2007-10-31
Maybe try addinging it to your session?

system->preferences->sessions. Click "new" and then enter your command into the "command" field and give it a name as well.

---

### Post by zlosynus on 2007-10-31
> **k0rfain said:**
> why didnt you just disable the desktop effects completly? :P

Because then it was terrible slow. I have X1400 graphic card and I dont know why, but it was just lagging all the time.

---

### Post by zlosynus on 2007-10-31
> **Thyme said:**
> Maybe try addinging it to your session?

system->preferences->sessions. Click "new" and then enter your command into the "command" field and give it a name as well.

No, it doesnt work, I already tried that.

---

### Post by Mr. Tos on 2007-10-31
Have a look at my thread:

[http://ubuntuforums.org/showthread.php?t=589557](http://ubuntuforums.org/showthread.php?t=589557)

Basically what's probably happening is that gnome is trying to start compiz still, but it's no longer there so no window manager is started. Changing the default manager in gconf-editor solved it for me.

---

### Post by zlosynus on 2007-10-31
Ok, but I also need to replace xserver-xgl with something not accelerated, that is not using GL. How can I make it?

---

