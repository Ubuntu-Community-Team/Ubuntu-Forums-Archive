---
title: "root popup"
date: 2006-07-17
forum: Desktop Environments
---

### Post by den_elze on 2006-07-17
hi,

I'm afraid that I've been messing with the permissions of /usr/bin /usr/sbin /bin and /sbin :s

is there a way to restore these permissions? Because now I'm not able to do anything administratif in gnome. The login as root popup does not appear.

thx

---

### Post by geco on 2006-07-17
> **den_elze said:**
> hi,

I'm afraid that I've been messing with the permissions of /usr/bin /usr/sbin /bin and /sbin :s

is there a way to restore these permissions? Because now I'm not able to do anything administratif in gnome. The login as root popup does not appear.

thx

Try to reset permission using a live CD, this works in most of cases ;)

---

### Post by aysiu on 2006-07-17
Try ```
sudo chown -R root:root /usr/bin
sudo chmod -R 751 /usr/bin
``` If you can't *sudo*, boot into recovery mode and use these commands: ```
chown -R root:root /usr/bin
chmod -R 751 /usr/bin
```

---

### Post by den_elze on 2006-07-19
thx for the reply

@aysiu
I'm affread this did not change anything :( I did not get an error message, but I still don't get a popup asking for root password

---

### Post by Ramses de Norre on 2006-07-19
What happens when you enter gksudo synaptic for example?

---

### Post by den_elze on 2006-07-19
Command not found :s

---

### Post by Ramses de Norre on 2006-07-19
I'm not sure which package it's in but could you try ```
sudo aptitude install gksu
``` and try the command again then.

---

