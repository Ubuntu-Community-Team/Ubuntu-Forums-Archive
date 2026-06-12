---
title: "Gedit problem"
date: 2006-08-02
forum: Desktop Environments
---

### Post by xander848 on 2006-08-02
I tried running the command: sudo gedit /etc/apt/sources.list and nothing happened. I any other commande with gedit in it does nothing. 
I tried using su and then the command but got:

(gedit:26264): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Any ideas on what to do?

---

### Post by Dylan103 on 2006-08-02
try sudo nano /etc/apt/sources.list

---

### Post by ardchoille on 2006-08-02
> **xander848 said:**
> I tried running the command: sudo gedit /etc/apt/sources.list and nothing happened. I any other commande with gedit in it does nothing. 
I tried using su and then the command but got:

(gedit:26264): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Any ideas on what to do?

It's not good to run graphical apps with sudo. Sudo is for command line apps.. gksudo is for graphical apps. The reason being that sudo can change files in your home directory causing you to not be able to log in at all. Use gksudo for graphical apps.

---

### Post by harsh on 2006-09-02
I have the same problem.

```

gksudo gedit

(gedit:17679): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.



```

If anyone knows a fix please tell :confused:

---

### Post by taurus on 2006-09-02
Are you sure you belong to the right groups before you run sudo or gksudo???  You need to be in groups adm & admin...

```
id
```

---

### Post by harsh on 2006-09-02
yes :) i think so ...

```

...~$ id

groups=4(adm)


```

---

### Post by taurus on 2006-09-02
> **harsh said:**
> yes :) i think so ...

```

...~$ id

groups=4(adm)


```
WRONG!!!  You need to belong to both groups adm & admin in Dapper...  So, you need to boot into the recovery mode (from GRUB menu) and edit your /etc/group.  Add yourself to group admin also...

```
nano /etc/group
```

---

### Post by harsh on 2006-09-02
Sorry i didnt answer your previous question truly. (my mistake)

```
Some of my /etc/group

adm:x:4:harsh
admin:x:112:harsh



```

---

