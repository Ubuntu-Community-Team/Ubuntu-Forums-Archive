---
title: "Xubuntu - Press shutdown sometime don't shutdown"
date: 2017-08-01
forum: Desktop Environments
---

### Post by kevin-smia on 2017-08-01
I use Xubuntu 16.04. Sometime when I press shutdown ( in the menu) it does not shutdown, nothing happen, the menu just close away, I have to press it the second time. I tried using command sudo shutdown -h now and init 0, both works fine at the first try. Any ideas? What command is the Xubuntu using on its menu for shutdown?

---

### Post by #&amp;thj^% on 2017-08-01
These are Xubuntu-specific: (Or XFCE4 session)

  
    *shutdown: **xfce4-session-logout --halt**
    *restart: **xfce4-session-logout --restart**
    *log out: **xfce4-session-logout --logout**
    *suspend: **xfce4-session-logout --suspend**
    *hibernate: **xfce4-session-logout --hibernate**

---

