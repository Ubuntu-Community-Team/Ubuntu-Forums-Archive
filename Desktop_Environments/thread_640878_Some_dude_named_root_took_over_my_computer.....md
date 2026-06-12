---
title: "Some dude named root took over my computer...."
date: 2007-12-14
forum: Desktop Environments
---

### Post by MarkoGT3 on 2007-12-14
So I want to edit etc/hosts, but it is read only. So I try to change that but it says that I can't because the owner is "root".

This frustrates be because I am the freakin' owner of the freakin' computer!!!

Of course I have lot to learn about linux, as this is probably resolved by simple command.

Anyway, can someone give me instructions on how to take over etc/hosts, so that I can change it?

Thx in advance...

---

### Post by AaronMiller on 2007-12-14
Run this command (ALT + F2):

gksudo gedit /etc/hosts

---

### Post by MarkoGT3 on 2007-12-14
Wow, it worked!

Thx alot!

---

### Post by bapoumba on 2007-12-14
You'll probably be interested in reading this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MarkoGT3 on 2007-12-14
Ok, i've bookmarked that. Thx

---

### Post by SunnyRabbiera on 2007-12-14
yell all the core files in your system are owned by the root user, even though it is you who is root you cannot just edit files in the core as you need to switch over to administration mode using sudo.
All linux operating systems have a root user you see, even ubuntu that uses sudo.
Only that in normal linux operating systems there is a main administration account (root) and there is you but in ubuntu they are sort of merged.
but to make sure no one messes your computer up (yes even you) all the core files are password protected and the only way to edit them is to use administration mode that you can operate in a terminal, currently there is no magic administration mode button yet, but leave it up to somebody to make one eh?

---

### Post by MikeyXX on 2007-12-14
Yah, understand  that                       Ubuntu

---

