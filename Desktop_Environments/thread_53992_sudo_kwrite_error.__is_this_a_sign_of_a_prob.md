---
title: "sudo kwrite error.  is this a sign of a prob?"
date: 2005-08-03
forum: Desktop Environments
---

### Post by jeffe on 2005-08-03
Hello all,

when i type "sudo kwrite", I get the following msg...

Error: "/var/tmp/kdecache-bob" is owned by uid 1000 instead of uid 0.
Aborting. $HOME not set!


and then it loads.  Is this a problem?  I've installed kubu several times this week and i hadn't seen this error before.

Also, shouldn't root be able to use that file regardless?  thanks...

---

### Post by cwaldbieser on 2005-08-03
I think it is experiencing schitzophrenic behavior because it wants to access some sort of configuration preferences for kwrite, but you are running as root (uid 0) instead of yourself (uid 1000).  It probably doesn't hurt anything, other than the fact your settings won't be saved.

---

### Post by jeffe on 2005-08-03
i actually had the configuration earlier prior to this but managed to fix that...

this one is for the cache...

---

### Post by yongyi on 2005-08-03
[QUOTE=jeffe]Hello all,

when i type "sudo kwrite", I get the following msg...

Error: "/var/tmp/kdecache-bob" is owned by uid 1000 instead of uid 0.
[/QUOTE]

I have this error too,and also:
```

root@ubuntu:/home/yongyi # kate thunderbird/DEBIAN/control
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-7316' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed. 

``` 
I don't know how to fix that.Any idea?

---

### Post by Takis on 2005-08-03
Kate has issues with sudo. You're better off using KWrite for files you want to edit as root.

---

