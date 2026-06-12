---
title: "Help I have broken GDM"
date: 2009-02-03
forum: General Help
---

### Post by surfgeek on 2009-02-03
I installed a new GDM login panel, rebooted then just a wait cursor. So tried sudo apt-get remove gdm which removed gdm but now I cannot reinstall gdm. I have just a text login screen no gui. Can I recover from the live install disc ?
thanks

---

### Post by phinullfermata on 2009-02-03
You could possibly try :

```
sudo aptitude install ubuntu-desktop
```

That might work... but not sure - it could also possibly use a lot of bandwidth...

---

### Post by blazemore on 2009-02-03
You can log in, and then use the startx command to load your desktop environment.
It's faster than GDM anyway

---

### Post by Yashiro on 2009-02-03
[http://ubuntuforums.org/showthread.php?t=1053810](http://ubuntuforums.org/showthread.php?t=1053810)

---

