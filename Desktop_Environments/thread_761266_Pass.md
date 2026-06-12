---
title: "Pass"
date: 2008-04-21
forum: Desktop Environments
---

### Post by GATOS45 on 2008-04-21
I lost my user & pass in my ubuntu pc and now how?
GATOS

---

### Post by kellemes on 2008-04-21
Boot from "Recovery Mode"

to find out the username..
```
ls -la /home
```

to set new password for this user (fill in your username)
```
passwd <username>
```

reboot.

---

### Post by opossumjack on 2008-04-21
If you have an indipendent /home partition, you could reinstall ubuntu using the same access name...

Or...

You should boot linux in RESCUE mode (or RECOVERY, I don't remember.. I'm at work and I don't have linux.. I will check it this evening :))

It should give you a root prompt or something like that.
Typer the  command

```
passwd [your username here]
```and substitute [your username here] with your user name.

If you don't remember your username you could find it with this command

```
 cat /etc/passwd | grep [your real name or just a piece of it]
```I hope it will help you..

Bye

---

### Post by opossumjack on 2008-04-21
Ok... kellemes answer is better than mine... 
eh eh eh...

:lolflag:

---

### Post by kellemes on 2008-04-21
> **opossumjack said:**
> 
```
 cat /etc/passwd | grep [your real name or just a piece of it]
```I

Indeed, this way you can search for a username too..

---

### Post by GATOS45 on 2008-04-21
I am new in ubuntu 
How i can boot from "Recovery Mode" or "rescue mode"

GATOS

---

### Post by opossumjack on 2008-04-27
At the GRUB menu, you should have your regular kernel choice and another with recovery mode written... I have it... Hope you have too...

---

