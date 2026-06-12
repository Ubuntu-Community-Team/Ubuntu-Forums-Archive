---
title: "[SOLVED] .bash_login breaks terminal colors"
date: 2009-01-04
forum: General Help
---

### Post by TestDummy! on 2009-01-04
I have a computer set up with Ubuntu Server 8.10 that I administer remotely over SSH with Putty. I noticed that if I do not have a .bash_login in my home folder, my terminal has colors when running commands such as 'ls'. When I create one with something in it (or even one that is empty), the colors in my terminal break. If I remove the file and login again, things are back to normal.

I'm beginning to think that when I have a .bash_login, I need to manually define my terminal colors, but I'm not entirely certain.

---

### Post by heindsight on 2009-01-04
I'm not entirely sure in where and how terminal colour is enabled, but I assume that it happens either in your .profile or in some script that gets called from ~/.profile and when you have a ~/.bash_login file then ~/.profile is not sourced when you log in.

(colour might be enabled from /etc/profile - i'm not sure if that is also not sourced if you have a ~/.bash_login)

---

### Post by TestDummy! on 2009-01-04
Tried putting the code I was placing in ~/.bash_login in ~/.profile instead and attempted another login. It runs the command as I wanted, and it doesn't appear to break the terminal colors either.

I figured the fix was easy enough, I just didn't know it ignored that file. Looking into it further, ~/.profile seems to call on ~/.bashrc, which has entries defining colors in the terminal.

Anyways, thanks for pointing that out.

---

### Post by heindsight on 2009-01-04
glad to have been able to help :)

---

