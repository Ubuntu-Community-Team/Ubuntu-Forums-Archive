---
title: "Chown command lost after restart"
date: 2009-06-21
forum: General Help
---

### Post by sim085 on 2009-06-21
Hello,

I am passing the following command:

chown -R vmail.daemon /var/run/courier/authdaemon/ 

However, after I restart the machine I find out the command is lost and that I need to pass it again. 

Why is this happening? and is there a way to make it stick? 

Regards,
Sim085

---

### Post by paperplate9 on 2009-06-21
Since your target appears to be in /var/run, which is usually stuff that get's created once a process starts running, when the process dies it probably removes those dir(s).

I don't know about your particular app (courier) but assuming it's a service, edit it's script in /etc/init.d to do the chown after it starts.

---

### Post by sim085 on 2009-06-21
> **paperplate9 said:**
> Since your target appears to be in /var/run, which is usually stuff that get's created once a process starts running, when the process dies it probably removes those dir(s).

I don't know about your particular app (courier) but assuming it's a service, edit it's script in /etc/init.d to do the chown after it starts.

Thank you :) I am new to linux and therefore I was thinking that run was just a normal directory as the others. 

Will do as you suggested :)

Regards,
Sim085

---

