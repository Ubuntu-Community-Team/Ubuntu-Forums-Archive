---
title: "changing ssh port"
date: 2009-06-06
forum: General Help
---

### Post by themacedonian on 2009-06-06
i like to change port for ssh. I like to do this for my personal save .

how to do this ?

---

### Post by iponeverything on 2009-06-06
Edit your:

```
/etc/ssh/sshd_config
```

You should know that a tool like nmap will show any outsider what port any service is listening on in about 2 minutes.

A good password is much more useful.

You also could use iptables to restrict access to that port to just IP addresses that you accessing it from.

Or restrict access to just key authentication.

---

### Post by themacedonian on 2009-06-09
i have used this comand:

```
sudo nano /etc/ssh/sshd_config
```
and change port from 22
now, when i changed port i dont know how to save list :S

help me :(

---

### Post by Hund on 2009-06-09
Ctrl + X and then "Y". To restart SSH:

> sudo /etc/init.d/ssh restart

---

### Post by themacedonian on 2009-06-09
port for ssh successfully changed :)

thanks

---

