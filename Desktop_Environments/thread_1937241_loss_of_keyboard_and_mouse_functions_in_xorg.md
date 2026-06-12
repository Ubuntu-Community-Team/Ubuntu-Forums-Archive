---
title: "loss of keyboard and mouse functions in xorg"
date: 2012-03-07
forum: Desktop Environments
---

### Post by carolinason on 2012-03-07
this issue occurs in a standard fresh install of xubuntu and sometimes in the livecd session. i lose the ability to use my keyboard and mouse effectively until i kill xorg and login a second time. after the initial login, whatever application i am using, i lose the ability to use the mouse to select anything out of that application and sometimes in the application. if i happen to be in a text field in the application, the keyboard allows me to type characters, but i have no alt-tab function. if i restart and i do not login at lightdm after about 30 minutes the bug doesn't seem to happen. also sometimes if i right-click in a non-focused application or the desktop it will sometimes free up the keyboard and mouse to act normally, but i lose them soon there after. i have to make sure and kill the initial xorg to have a normally functioning desktop and this works 99% of the time. sometimes i have to kill it twice, but that is rare.

this happens in a default install of debian + xfce as well. it also happens in kubuntu. 

i have tried different keyboards and mice.

i never have the issue if i log into xorg as root.

the bug appeared after a kernel update and then went away after another kernel update, but has reappeared.

---

### Post by carolinason on 2012-03-07
oh yeah. the problem started in debian wheezy and occurs in the updated current xubuntu 11.10 and 12.04

---

### Post by carolinason on 2012-03-07
i must not have changed the mouse, i knew i changed the keyboard, but it seems to be a logitech wireless unit(perhaps a driver for it). odd thing is killing xorg or logging in as root as well as running old versions of linux fixed the thing. will mark solved.

/* edit -- this turned out to be a logitech wireless kbd+mouse problem. model c e0682 kbd+mouse combo and it works fine in older versions of linux, so i am not sure if it's hardware or software related.

---

