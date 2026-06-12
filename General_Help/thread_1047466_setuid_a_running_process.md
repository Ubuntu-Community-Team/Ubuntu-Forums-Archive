---
title: "setuid a running process"
date: 2009-01-22
forum: General Help
---

### Post by kerneldaemon on 2009-01-22
Hello, this is my first post.

Is it possible to change the permissions of an already running process ?

Example:

            Suppose I'm viewing /etc/fstab with emacs using 
            an ordinary user account. Suddenly I want to change
            something. can I chown emacs from another virtual
            root consol without restarting emacs ?

Thank you,

---

### Post by snova on 2009-01-22
I don't think so...

---

### Post by mssever on 2009-01-22
Programs running as root are able to drop privileges (presumably by calling fork(), though I don't really know), but I don't think that privilege escalation is possible unless you manage to exploit a security vulnerability.

---

### Post by kerneldaemon on 2009-01-23
Well that's quiet obvious. Imagine if you could spawn a root shell on a remote machine, exploitinig some vulnerability, you could change root GID's while keeping them running, ewwwww !

AnyWay, but there must be someway to doing it for some reason or other. Suppose you messed up with GID of a million tera thing Oracle DataBase by forbidding a particular group from write privilege, and the data base can't for no excuse be shutdown !

How would one figure out a suitable solution then ?

---

### Post by mssever on 2009-01-23
> **kerneldaemon said:**
> Well that's quiet obvious. Imagine if you could spawn a root shell on a remote machine, exploitinig some vulnerability, you could change root GID's while keeping them running, ewwwww !

AnyWay, but there must be someway to doing it for some reason or other. Suppose you messed up with GID of a million tera thing Oracle DataBase by forbidding a particular group from write privilege, and the data base can't for no excuse be shutdown !

How would one figure out a suitable solution then ?
Perhaps you could temporarily chown the files Oracle needs to write. But that kind of mistake would probably be quite messy. At any rate, Oracle *should* refuse to start if it can't write its data to disk--or at least it should go into read-only mode. I've never used Oracle, so I have no idea how it actually works.

---

