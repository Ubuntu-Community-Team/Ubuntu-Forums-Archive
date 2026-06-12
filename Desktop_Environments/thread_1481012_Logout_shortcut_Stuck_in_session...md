---
title: "Logout shortcut? Stuck in session.."
date: 2010-05-12
forum: Desktop Environments
---

### Post by earthtoclinton on 2010-05-12
Hi all,

For some stupid reason I installed the new unity interface on my computer for a peek (lucid). When I logged in I was greeted simply with a blank screen showing my wallpaper. I am unable to log out to choose either my gnome or Lxde sessions. Obviously everytime I restart it goes straight back into the blank unity session...I tried ctrl+alt+delete, which brings up the shutdown menu, but it doesn't have a logout option. Any help would be great!!

---

### Post by mimor on 2010-05-12
If you do Alt+F2 and type gnome-terminal, can you bring up a terminal that way?

---

### Post by mhgsys on 2010-05-12
press ctrl+alt+f1 

Login on the tty with your username and password. 

once logged in type; 
```
sudo /etc/init.d/gdm stop
```
followed by your password;

(this will stop gdm / x)

then to get it running again type;
```
sudo /etc/init.d/gdm start
```

---

### Post by earthtoclinton on 2010-05-12
mimor, unfortunately your option has no effect, but thanks anyway. mhgsys I tried your approach - as soon as I hit ctrl+alt+f1 it seems to do something, but then goes to a blank screen indefinitely, as if in hibernation or something. Thanks for the help..If I have screwed it somehow I guess I'll just re-install..

---

### Post by earthtoclinton on 2010-05-13
Sorry to be a pain and bump, just wondering if anyone else has any ideas before I look at doing a re-install. Cheers

---

### Post by night1727 on 2010-07-30
i have this same problem but the screen shows the dectop flashing and when i try to do thing it resets it.

---

### Post by hariks0 on 2010-07-31
May not be of assistance right now, but you can try the link at my signature later after reinstall.

---

