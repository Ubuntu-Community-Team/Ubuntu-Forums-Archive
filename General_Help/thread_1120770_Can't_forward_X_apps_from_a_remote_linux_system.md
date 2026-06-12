---
title: "Can't forward X apps from a remote linux system"
date: 2009-04-09
forum: General Help
---

### Post by taev on 2009-04-09
I'm trying to forward X applications (like gvim) from a remote redhat host to my local ubuntu 8.10 system. I've edited gdm.conf to say DisableTCP=false. I'm logging into the remote system via ssh -X hostname. I still receive the following:

> david@quark:~$ xcalc
No protocol specified
Error: Can't open display: 10.11.15.126:0.0
david@quark:~$ xcalc -TCP
No protocol specified
Error: Can't open display: 10.11.15.126:0.0
david@quark:~$ xcalc -display 10.11.15.126:0.0
No protocol specified
Error: Can't open display: 10.11.15.126:0.0


Quark is the remote host. .126 is my local machine. Help?

---

### Post by kanikilu on 2009-04-09
Are you sure X11 forwarding is enabled on the server? Also, maybe try ssh -Y instead of -X?

---

### Post by taev on 2009-04-09
> **kanikilu said:**
> Are you sure X11 forwarding is enabled on the server? Also, maybe try ssh -Y instead of -X?

Other distros are able to forward X sessions from the machine without issue. I've tried both -Y and -X, no help.

---

### Post by kanikilu on 2009-04-09
Hmm, this works for me, and I have DisallowTCP=true in gdm.conf...

Is xauth installed? See if this returns anything: ```
ps -ef | grep Xauth
```

---

### Post by taev on 2009-04-09
That command yields the following:

> root     25201 25192  4 10:15 tty9     00:03:12 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt9

---

