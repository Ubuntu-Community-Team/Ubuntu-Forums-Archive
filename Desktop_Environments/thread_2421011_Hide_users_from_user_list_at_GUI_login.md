---
title: "Hide users from user list at GUI login"
date: 2019-06-14
forum: Desktop Environments
---

### Post by kpatz on 2019-06-14
On 18.04, when I log in to the desktop, I get a list of available users.  I don't want to disable the list entirely, but I don't want all the users to appear either... just mine.

I tried disabling the additional accounts (none are currently in use, but I want to keep them because of samba ownership/permissions) using **usermod --expiredate 1 username** and that prevents them from logging in, but they still show up in the list.

Is there a way to hide users, or only show specified users, on the list?  This is the normal Ubuntu gnome desktop running in gdm3.  I tried adding these lines to /etc/gdm3/custom.conf:```
[greeter]
IncludeAll=false
Include=kpatz

```but that had no effect.

---

### Post by dino99 on 2019-06-15
An old topic that needs adaptation (lightdm/gdm3 path)  [http://www.askmeaboutlinux.com/?p=1886](http://www.askmeaboutlinux.com/?p=1886)

---

### Post by kpatz on 2019-06-15
That shows how to make the list disappear completely so you have to type in your user name.  I did that by editing** /etc/gdm3/greeter.dconf-defaults** and uncommenting these two lines:

```
[org/gnome/login-screen]
...
disable-user-list=true
```

I was wondering if there was a way to keep the list but only show specified users, or hide specified users.

**EDIT:  I found a solution! ** Locking the password on an account with **sudo passwd -l username** will stop the user from showing up on the list.  It doesn't seem to affect samba access either.  Nice.  Marked solved.

---

