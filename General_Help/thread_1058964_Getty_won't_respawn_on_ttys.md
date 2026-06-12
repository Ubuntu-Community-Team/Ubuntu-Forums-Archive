---
title: "Getty won't respawn on ttys"
date: 2009-02-03
forum: General Help
---

### Post by MarkHowells on 2009-02-03
I have a fairly vanilla 8.10 server installation. I've made no config changes to the login process. We generally ssh onto the box via openvpn and that works fine. However occasionally I had to resort to the console and I've noticed that when I login through a tty and then logout the getty is not respawned. Basically this means I have 6 tty logins before I need to reboot !! ;)

here's /etc/event.d/tty1

```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1
```
What can be preventing a respawn of getty ?

Cheers

Mark

---

### Post by chiefbutz on 2009-02-03
Your /etc/event.d/tty1 looks the same as the one I have on my server, so I don't think that is the problem.

---

### Post by MarkHowells on 2009-02-09
bump

---

### Post by Ciantic on 2009-02-13
Ubuntu 8.10 (Desktop!), installed few days ago. Gettys does not respawn.

I have ttys 4, 5 and 6 left, any ideas? Before I have to reboot too.

Should we file a bug?

Btw, how do I know my system even runs /etc/event.d/tty1 for instance? I'm not that convinced that it is running, or were even started. All files in /etc/event.d/ are nonexecutable, on the otherhand /etc/init.d/ all files are executable? Why such difference?

> 
jarppa@jarppa-laptop:/etc/event.d$ ls -la
total 96
drwxr-xr-x   2 root root  4096 2008-10-30 01:15 .
drwxr-xr-x 138 root root 12288 2009-02-13 15:11 ..
-rw-r--r--   1 root root   260 2008-09-30 02:52 control-alt-delete
-rw-r--r--   1 root root   187 2008-10-22 03:16 last-good-boot
-rw-r--r--   1 root root   299 2008-09-30 02:52 logd
-rw-r--r--   1 root root   552 2008-09-30 02:52 rc0
-rw-r--r--   1 root root   342 2008-09-30 02:52 rc1
-rw-r--r--   1 root root   403 2008-09-30 02:52 rc2
-rw-r--r--   1 root root   403 2008-09-30 02:52 rc3
-rw-r--r--   1 root root   403 2008-09-30 02:52 rc4
-rw-r--r--   1 root root   403 2008-09-30 02:52 rc5
-rw-r--r--   1 root root   422 2008-09-30 02:52 rc6
-rw-r--r--   1 root root   485 2008-09-30 02:52 rc-default
-rw-r--r--   1 root root   392 2008-09-30 02:52 rcS
-rw-r--r--   1 root root   575 2008-09-30 02:52 rcS-sulogin
-rw-r--r--   1 root root   558 2008-09-30 02:52 sulogin
-rw-r--r--   1 root root   306 2008-09-30 02:52 tty1
-rw-r--r--   1 root root   300 2008-09-30 02:52 tty2
-rw-r--r--   1 root root   300 2008-09-30 02:52 tty3
-rw-r--r--   1 root root   300 2008-09-30 02:52 tty4
-rw-r--r--   1 root root   300 2008-09-30 02:52 tty5
-rw-r--r--   1 root root   300 2008-09-30 02:52 tty6


> 
jarppa@jarppa-laptop:/etc/event.d$ ps -u root | /bin/grep "tty"
 4276 tty4     00:00:00 getty
 4277 tty5     00:00:00 getty
 4286 tty6     00:00:00 getty
24620 tty7     01:27:47 Xorg


---

### Post by Ciantic on 2009-02-13
Found a temporary fix:

"sudo start tty1"

And now tty1 respawns again!

Though, I have no clue why it doesn't do so by default.

---

### Post by lintoolman on 2009-02-23
I had the same issue and here is how I fixed it on my Ubuntu 8.10 server.

I discovered there was no .bashrc in my profile.  So I copied root's .bashrc to my home directory and chmod/chown the file as approriate and now it works just fine.

---

### Post by Yhetti on 2009-03-06
I'm having the same problem.  It just started today, and I think it may be involved with installing Truecrypt, although it could be just a coincidence.  This is an 8.10 server as well.

For what it's worth, you can respawn the other TTY's by hand by doing something like

getty 38400 tty1 &

For each of the tty's that are dead.  This isn't a fix, but it'll let you log in again.

More importantly, why did Linux vendors decide to move to the eventd system for something as critical as tty spawn when there is -no way- to force eventd to restart, as it's a kernel thread?

Bad!

---

### Post by Ciantic on 2009-03-22
> **Yhetti said:**
> For what it's worth, you can respawn the other TTY's by hand by doing something like

getty 38400 tty1 &


that is incorrect way, please use:
"sudo start tty1" (or replace 1 with number that is stuck)

---

### Post by Cefiar on 2009-06-18
I had this problem with a new 9.04 setup.

After much mucking around, I eventually discovered a way around it.

I edited the file /etc/default/rcS and changed 'DELAYLOGIN=no' to 'DELAYLOGIN=yes'.

This is supposed to stop the getty's starting till AFTER all the other processes in the current runlevel have started.

My suspicion is that upstart is starting the getty's before something in /etc/init.d/ is run (as called by the /etc/rc2.d/ symbolic links), which cuts off the communication mechanism to the getty's from upstart somehow.

---

