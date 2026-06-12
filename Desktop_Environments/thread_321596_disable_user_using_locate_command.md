---
title: "disable user using locate command"
date: 2006-12-19
forum: Desktop Environments
---

### Post by denday on 2006-12-19
Hi.

anyone know how to disable user using locate command. 

i've use chmod command to limit user permission, but locate command can execute that file and read it even read only.

any help appreciated.

---

### Post by mlind on 2006-12-19
if /etc/updatedb.conf doesn't support privileged usage, then you can always use /etc/sudoers (edit using **visudo** only) to allow only certain users to use the command.

---

### Post by paparucino on 2006-12-19
> **denday said:**
> Hi.

anyone know how to disable user using locate command. 

i've use chmod command to limit user permission, but locate command can execute that file and read it even read only.

any help appreciated.
You should rename locate to another filename ;-)

---

### Post by denday on 2006-12-19
can you give me some example... :mrgreen:

---

### Post by paparucino on 2006-12-19
> **denday said:**
> can you give me some example... :mrgreen:
In a terminal
```
mv /usr/bin/locate /usr/bin/the name you want
```
before doing this I suggest to do
```
cp /usr/bin/locate /usr/bin/X_locate
```
so you can restore the original name with this sopy if something goes wrong

---

