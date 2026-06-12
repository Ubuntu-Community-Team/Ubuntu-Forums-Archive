---
title: "Prevent xfce4 from starting as well as the login window"
date: 2010-09-07
forum: Desktop Environments
---

### Post by srudes2 on 2010-09-07
Hello all!
I would like to know how to prevent the xfce4 from starting as well as the login window. 
I just want my tty7 just like my tty6. However I do want to be able to start xfce4. 
Any idea's on how to set this up?

Thank you

Martin

---

### Post by srudes2 on 2010-09-07
After looking for a few hours... I finally found the answer here:
[http://ubuntuforums.org/showthread.php?t=1499167](http://ubuntuforums.org/showthread.php?t=1499167)

Just move the init gdm configuration file:
```
mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec
```

After you've done that reboot xubuntu. When xubnutu starts you'll be on tty1. If you want to start xfce4 simply login(no root) and enter the command startx. Your desktop will look different from before, but you can change the style back by going to system-settings.

---

