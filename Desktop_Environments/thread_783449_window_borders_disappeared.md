---
title: "window borders disappeared"
date: 2008-05-05
forum: Desktop Environments
---

### Post by mikiek on 2008-05-05
Hi,

I have a big problem with Xubuntu 8.04. I upgraded from 7.10 immediately after 8.04 was released. Suddenly (2008-05-02) window borders (plus window title) disappeared. In that moment I tried to return from virtual machine in VMPlayer by pressing "Ctrl+Alt+R". When I wanted to try something with "Settings->Settings Manager->Window Manager I received message: "these settings cannot work with your current window manager (unknown)" Lower toolbar has no signs of opened windows, nor icons for workplaces. Upper toolbar is bellow opened window. I have set "I allow XFCE to manage my desktop". Strange behaviour. Now I cannot move/resize/max/min windows.

Please help,
Best regards,
Milos

---

### Post by linux phreak on 2008-05-05
Type,   xfwm4 --replace   after pressing alt+f2.It brings up the run dialog box.

---

### Post by mikiek on 2008-05-06
great..now it works..really thanks
Milos

---

### Post by th_agorastos on 2009-12-28
Indeed it works fine! The thing that bothers me is that in my Xubuntu 9.10, my default user account does not render either of the taskbars on top and on the bottom of the screen no matter what I did (restart PC). I even tried creating a new user account just to be sure that there is no part of the user-specific configuration and guess what! For the new user, the task bars were rendered correctly, but I couldn't see any windows title bars and buttons!

It seems that some services did not run successfully. Any ideas about this?

---

### Post by denham2010 on 2010-03-20
> **th_agorastos said:**
> Indeed it works fine! The thing that bothers me is that in my Xubuntu 9.10, my default user account does not render either of the taskbars on top and on the bottom of the screen no matter what I did (restart PC). I even tried creating a new user account just to be sure that there is no part of the user-specific configuration and guess what! For the new user, the task bars were rendered correctly, but I couldn't see any windows title bars and buttons!

It seems that some services did not run successfully. Any ideas about this?

You need to re-start your panels:

In a terminal , or ALT + F2 enter:

```
xfce4-panel &
```

---

### Post by rana_mum on 2011-01-27
[LEFT]xfwm4 sure worked!!!:P:P

however, one more help pls...
my mouse pointer chooses any one icon on the screen and sticks to it...this triggers random opening of many windows of one type....

help...please:(
[/LEFT]

---

