---
title: "Starting an application on a remote machine GUI session"
date: 2009-04-15
forum: Desktop Environments
---

### Post by crismdq on 2009-04-15
Hi!

Lets say i on my work and want to start for example "amule" on the ubuntu located in my home. I log into my home computer and type

```
# amule
```

getting

```
Error: Unable to initialize gtk, is DISPLAY set properly?
```

My question is, how can i tell the remote ubuntu to open "amule" on the already opened gnome session in that computer.

Same happend with any app thats need GUI, like picasa for example.

```
# picasa
ERROR: Couldn't open display.

```

Regards

---

### Post by PacSci on 2009-04-15
First, I'd suggest typing 'w'. It will list something like:

```
 21:54:37 up  1:32,  2 users,  load average: 0.48, 0.53, 0.48
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
leaf     tty7     :0               20:22    5:32   4:23m  0.24s x-session-manager
leaf     pts/0    :0.0             20:23    0.00s  0.76s  0.00s w

```

Look for the one named x-session-manager, and check its "FROM" field. Then, type "export DISPLAY=':0'", replacing :0 with the actual FROM entry. No guarantees, as I can't exactly replicate your circumstances, but it should work.

---

### Post by crismdq on 2009-04-16
Thanks! It works perfect!

---

