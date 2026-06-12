---
title: "Hostname not showing properly?"
date: 2010-02-27
forum: Desktop Environments
---

### Post by vksingh on 2010-02-27
Hi,

I am using Ubuntu 9.10. I changed the hostname by editing the file:

/etc/hostname.

But, still it is showing old hostname in the prompt. I want to know which service should I restart to reflect the change in Hostname.

Thanks,

Vivek

---

### Post by jswoods7 on 2010-02-27
If you don't want to restart, just run 'hostname <new hostname>'

---

### Post by vksingh on 2010-02-27
Hi, 

But even then , the prompt is coming like this:

vivek@old_hostname#

I want it to be:

vivek@new_hostname#

Thanks,

Vivek

---

### Post by jswoods7 on 2010-02-27
You'll need to restart your shell:

```
root@old-hostname:~# hostname new-hostname
root@old-hostname:~# bash
root@new-hostname:~# exit
exit
root@old-hostname:~# 
```

---

### Post by efflandt on 2010-02-28
I made the same mistake.  You forgot to also edit /etc/hosts

You probably need to log out of X and log back in, because X uses network sockets.

---

