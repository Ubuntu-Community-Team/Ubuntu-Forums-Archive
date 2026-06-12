---
title: "Administration Problems"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Falcon X on 2006-09-17
I am having a problem trying to open any administrative programs.  They all start booting, but never open up/load.  Does anyone have any ideas on how to correct this?

---

### Post by ciscosurfer on 2006-09-17
Are you logging in as the user you created during the install?

---

### Post by Falcon X on 2006-09-17
Yes.

---

### Post by ciscosurfer on 2006-09-17
Go to add/remove users, select your username, and reset your password.

---

### Post by Falcon X on 2006-09-17
Unfortunately I cannot open up the Users and Groups Dialog.

---

### Post by ayoli on 2006-09-17
```
passwd your_username
```
if cant sudo look here: [http://psychocats.net/ubuntu/sudo](http://psychocats.net/ubuntu/sudo)

---

### Post by ciscosurfer on 2006-09-17
Sorry.  You obviously can't.  Ok.   Try using  'passwd' at the command line.

---

### Post by Falcon X on 2006-09-17
I can change my password, but when I try and sudo I get this message:

unable to lookup blackbox via gethostbyname()

blackbox is the name of my computer.

---

### Post by Falcon X on 2006-09-17
Okay, so I went throught that sudo page that was given.  My two sudo files (/etc/group, etc) are fine.  The username I am using is a member of the admin group, and the admin group has the permission to sudo.

---

### Post by ayoli on 2006-09-17
> **Falcon X said:**
> I can change my password, but when I try and sudo I get this message:

unable to lookup blackbox via gethostbyname()

blackbox is the name of my computer.

reboot in recover mode, then edit thse files

```
nano /etc/hostname
```
add on first line your hostname (blackbox) if it not here, then CTRL+X and *yes* to quit and save, then:```

sudo nano /etc/hosts
``` you must have this as first line (if not add it)
```
127.0.0.1 localhost blackbox
```
reboot in normal mode and try sudo again

---

