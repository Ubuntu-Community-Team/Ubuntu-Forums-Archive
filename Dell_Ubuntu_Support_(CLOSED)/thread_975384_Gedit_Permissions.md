---
title: "Gedit Permissions"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bd_thompson on 2008-11-08
Is there a way to give Gedit root permissions with root's password like other GUI applications?  

I'd like to be able to edit files such as HOSTS without resorting to Terminal.

---

### Post by mattze on 2008-11-08
```
gksu gedit
``` ?

---

### Post by bd_thompson on 2008-11-08
> **mattze said:**
> ```
gksu gedit
``` ?

Not quite.  It and sudo allows edit of root's files (HOSTS) with Gedit only after root's password has been entered in another application such as root terminal.  

Thanks.

---

### Post by Raouf on 2008-11-08
> **bd_thompson said:**
> Not quite.  It and sudo allows edit of root's files (HOSTS) with Gedit only after root's password has been entered in another application such as root terminal.  

Thanks.

What's the Difference between sudo n gksu
thx for assistance

take care
- Raouf

---

### Post by mattze on 2008-11-08
if I understand it correctly gksu should be used for GUI applications - sudo can mess up your configuration.

running ```
gksu gedit
``` from the application starter (ALT + F2) will ask for your root password and start gedit with root privileges. i thought that is your aim... 

maybe you can clearify...

---

### Post by Cannaregio on 2008-11-08
Using sudo can break things: certain files' ownership can become set to root, because when sudo launches an application, it launches (sometimes) with root privileges but uses the user's configuration file.

Use ```
gksudo gedit
``` instead
Note that's [COLOR="Blue"]gksudo[/COLOR], not [COLOR="#0000ff"]gksu[/COLOR]

Anyway, rule of thumb is
sudo for cli applications
gksudo for graphical applications

Most of the time this isn't an issue. A lot of applications WILL run the improper way: you use sudo for graphical applications and see no adverse side effects... there are times, though, when side effects can occur: as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because some permissions changed. You can read a full discussion on the issue [here]("http://www.mail-archive.com/arch@archlinux.org/msg04963.html"). 

Cheers!

---

### Post by mattze on 2008-11-08
why gksudo and not gksu?

---

### Post by Cannaregio on 2008-11-08
[COLOR="Blue"]gksu[/COLOR] is a frontend to su and [COLOR="#0000ff"]gksudo[/COLOR] is a frontend to sudo. Unlike su, sudo changes your permissions for only a single command.

---

