---
title: "Icewm awesome fast but doesnt shutdown"
date: 2006-07-20
forum: Desktop Environments
---

### Post by T31 on 2006-07-20
Hi guys,

Everyone should try icewm after a couple of tricks can look this good [http://photos1.blogger.com/blogger/1987/995/1600/2006-04-23-193416_1024x768_scrot.png]("http://photos1.blogger.com/blogger/1987/995/1600/2006-04-23-193416_1024x768_scrot.png")

ok ok I know I have to work more the fonts of Eterm when I have it fully transparent, but anyway to the point,

I cant shutdown with the button of the menu I have to do it or thru the terminal or logging out and then from gdm](*,) 

Any ideas over there?:-k

---

### Post by aysiu on 2006-07-20
There should be a shutdown option in the menu. Otherwise, you can do ```
sudo shutdown -h now
```

---

### Post by az on 2006-07-20
Yeah, you have to log out and use the session manager to shutdown.

Icewm does not do any authentification.  You would have to configure the shutdown command in the incewm config and then set the sudo rights to that command to NOPASSWD so that you don't have to enter a password.  Bummer.

---

### Post by BLTicklemonster on 2006-12-02
Shut down? I can't even log out! I have to restart _X_term, then close that window to log out. Anyone know a way to log out? I'm in feisty, though edgy does the same thing (I have both). It used to work okay on dapper.

---

