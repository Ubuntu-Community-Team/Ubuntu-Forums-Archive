---
title: "Log ubuntu in text command"
date: 2009-03-22
forum: General Help
---

### Post by kut77less on 2009-03-22
I just turned of graphical log in by going to system services. When I restart the computer it starts up, and it asks me my user name and password. When I enter the information it does not log in I just get a terminal command line


$my username 


What do I do next to use the computer

---

### Post by taurus on 2009-03-22
```
startx
```
Unless you want to do everything from a prompt.

---

### Post by kut77less on 2009-03-22
I did do that, but there is some error

---

### Post by taurus on 2009-03-22
Want to share the error messages when you run **startx**?

---

### Post by urd on 2009-03-22
> **taurus said:**
> Want to share the error messages when you run **startx**?

i have the same problem

when i do that  show me some driver that linux can load, those are mi video card drivers, what can i do?

---

### Post by taurus on 2009-03-22
> **urd said:**
> i have the same problem

when i do that  show me some driver that linux can load, those are mi video card drivers, what can i do?

How about

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by kut77less on 2009-03-22
> **taurus said:**
> Want to share the error messages when you run **startx**?

When I run I get this error 

> X:/ tmp/ X||-unix has suspicious ownership (not root, root), aborting 

Xinit: server error

I try to log in as root (su), but I get the same error. How do I fix this. Can I just enable graphic log in the command line

---

### Post by taurus on 2009-03-22
> **kut77less said:**
> When I run I get this error 



I try to log in as root (su), but I get the same error. How do I fix this. Can I just enable graphic log in the command line

What's the output of this command?

```
ls -la /tmp
```

---

### Post by urd on 2009-03-22
> **taurus said:**
> How about

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

i try that, and this shows

```
xserver-xorg postinst warning: overwriting  possibly customised configuration file; backup in etc/x11/xorg.conf.20090322142019
```

> What's the output of this command?


```
ls -la /tmp
```
```
total 16
drwxrwxrwt 4 root 4096 2009-03-22 14:20 .
drwxr-xr-x 20 root 4096 2009-03-15 23:45 ..
drwxrwxrwt 2 root 4096 2009-03-22 14:18 .ICE-unix
drwxrwxrwt 2 root 4096 2009-03-22 14:19 .X11-unix
```

---

