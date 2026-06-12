---
title: "X permissions defaults (opening windows as root)"
date: 2005-11-23
forum: Desktop Environments
---

### Post by beijingjj on 2005-11-23
I like to su to root and do stuff there rather than typing sudo before each command.  However when I try to spawn a window I get this message: 
```
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
emacs: Cannot connect to X server :0.0.
Check the DISPLAY environment variable or use `-d'.
Also use the `xhost' program to verify that it is set to permit
connections from your machine.

```
until I go into my normal, non-priviledged user's window and type:
```
xhost +

```
How can I make it so that root can connect to X automatically each time?

---

### Post by aysiu on 2005-11-23
I don't know if I understand your question completely, but can't you just run the command ```
kdesu konqueror
```?

---

### Post by beijingjj on 2005-11-25
[QUOTE=aysiu]I don't know if I understand your question completely, but can't you just run the command ```
kdesu konqueror
```?[/QUOTE]

I'm not familiar with this command, but it appears to be similar to "sudo."  At any rate, this doesn't seem to help.

Let me try to make my question simpler.  When I start a terminal, I type "su" to become root.  Then I want to run X applications like "gedit" or "make xconfig" (on the kernel), etc.  Root by default does not have permission to connect to the X server.  How do I give root permission to connect to the X server by detault?

---

