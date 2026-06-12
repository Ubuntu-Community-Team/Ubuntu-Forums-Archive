---
title: "Ubuntu and Beryl"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by LeoKnight on 2007-08-31
Ive just installed Beryl, and how do i use the effects please and the cube, ive enabled desktop wobbling but nothink happens >< 

thanks

/Kev

---

### Post by Amazona aestiva on 2007-08-31
Beryl shold be in Apps.-> System tools
However you can start it from terminal:
```
beryl-manager
```

---

### Post by LeoKnight on 2007-08-31
> **Amazona aestiva said:**
> Beryl shold be in Apps.-> System tools
However you can start it from terminal:
```
beryl-manager
```

when i start it from terminal says it cannot be found >< but its in Apps -> system tools
ive configured it from there but still doesnt work :| any ideas please?

---

### Post by Amazona aestiva on 2007-08-31
Try:
```
sudo apt-get install --reinstall beryl beryl-manager
```

---

### Post by LeoKnight on 2007-08-31
> **Amazona aestiva said:**
> Try:
```
sudo apt-get install --reinstall beryl beryl-manager
```

nope its the same, saying the same :(

also - when i try logging into root user it says "cannot log in as root user here" ><

---

### Post by Amazona aestiva on 2007-08-31
Beryl in the add/remove apps too try install it from there.(system tools)
No...Have You installed it from there?

Hmm... It seems the real problem is that You can't use sudo?... aren't you an administrator?

---

### Post by CureDimz21 on 2007-08-31
yeah.  when you do it from the terminal, doesn't it ask you for a password?  if you don't have the password it won't work.  it's gonna be the same thing, but try starting synaptic package manager and searching for beryl
System---> Administration---> Synaptic Package Manager
again, it will ask for the password.  if this is your comp, shouldn't you have it?  if someone set this up for you, ask them what the root password was set to when they installed.

---

### Post by LeoKnight on 2007-08-31
I'm using Wubi to install Ubuntu coz my HD isnt letting me partition it, also it doesnt let me log in using root >< for some reason >< i installed it on user root i think, i think thats my problem

Edit: yeah it does ask for a password when i use administrator programs

---

