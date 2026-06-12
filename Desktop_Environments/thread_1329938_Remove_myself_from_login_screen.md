---
title: "Remove myself from login screen"
date: 2009-11-17
forum: Desktop Environments
---

### Post by Oceanwatcher on 2009-11-17
I just finished installing Xubuntu on an old P3 for a friend and things are running very ok. But to avoid any confusion, I would like to remove myself from the login screen.

The way it was in 9.04 was actually a lot better than the way it is in 9.10 in my opinion. If there was a setting to switch to that login screen instead, I would do that.

Xubuntu 9.10

---

### Post by CylnZ on 2009-11-18
Hi, I also find the new login window foolish. If I wanted a windows login, I'd run windows...
This worked for me last night. It's ugly, but it IS a graphical login screen where there is no user list. You log in just like in 9.04, but you have to hit "ENTER" first, then login

```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
```

---

