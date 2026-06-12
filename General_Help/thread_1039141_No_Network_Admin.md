---
title: "No Network Admin"
date: 2009-01-14
forum: General Help
---

### Post by airjaw on 2009-01-14
Hello, wondering if I can get some light shed on a problem I have.

(8.10 on Gnome)

I have no Network option under 
Systems -->> Administration -->> ( Network )

The closest I have is Network Tools. I wanted to rename my computer and thats when I discovered this issue.

from the CLI, gksudo network-admin doesn't work either. It prompts me for my password, then fails to actually open.

Can anyone shed some light on this?  Also, is there some place I can look on the file system, some logs perhaps, that will give me more info about what is going wrong when things fail to open?

Thanks.

---

### Post by adult swim on 2009-01-14
edit:  dont try my previous advice.

---

### Post by airjaw on 2009-01-14
Thats ok.. well thanks for trying :)

---

### Post by adult swim on 2009-01-14
if you did it and it broke your machine, it is easily fixable. hopefully i edited in time.
the hostname is located at /etc/hostname and you can change it from there.  i thought you also have to change the hostname in /etc/hosts to match it but even after i did that i was unable to open any programs.  im sure someone will come along who knows what is going on.

---

### Post by airjaw on 2009-01-14
Thanks, yes the renaming computer through /etc/hostname was actually in another thread I started. I had the same problem with not being able to open any programs after renaming.

I tried renaming several times and for some reason the last time I tried it, it worked after a restart.

However, there is still the mystery of why I have no "Network" or 'network-admin' that everyone else seems to have, and thats where this thread comes along :)

---

