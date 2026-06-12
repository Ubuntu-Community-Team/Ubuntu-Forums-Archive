---
title: "XForwarding probglems"
date: 2006-03-04
forum: Desktop Environments
---

### Post by underwater on 2006-03-04
I'm trying to use xforwarding and I"m not getting it working at all.

As soon as I ssh over with ssh -X

the first error message appears

/usr/bin/xauth:  /home/whatever/.Xauthority not writable, changes will be ignored


I try to start something like xterm and I get

X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


I've been googling around but I haven't found anything to help out.  I've done the basics as far as I know, change sshd conf adding XForwarding and stuff like that.  


Any ideas?


Thanks in advance,

---

### Post by art on 2006-03-04
What are the permissions of .Xauthority? Mine is 
-rw-------

---

### Post by cwaldbieser on 2006-03-04
[QUOTE=underwater]I'm trying to use xforwarding and I"m not getting it working at all.

As soon as I ssh over with ssh -X

the first error message appears

/usr/bin/xauth:  /home/whatever/.Xauthority not writable, changes will be ignored


I try to start something like xterm and I get

X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


I've been googling around but I haven't found anything to help out.  I've done the basics as far as I know, change sshd conf adding XForwarding and stuff like that.  


Any ideas?


Thanks in advance,[/QUOTE]

Try using the -Y option instead.

---

