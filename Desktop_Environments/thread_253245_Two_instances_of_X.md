---
title: "Two instances of X"
date: 2006-09-08
forum: Desktop Environments
---

### Post by lozenge on 2006-09-08
Two instances of X are running on tty7 and tty9, subsequently rendering me unable to run Xgl.

```
james@monkey:/usr/src$ ps -e|grep X
 4393 tty7     00:02:48 Xorg
 4620 ?        00:00:00 Xgl
 4632 tty9     00:00:06 Xorg

```

Any clue as to why? I'm completely puzzled.

---

### Post by encompass on 2006-09-08
could be you have logged in twice.  Do this showup at boot?

---

### Post by lozenge on 2006-09-08
Yeah, the first instance of Xorg starts, then after about 5 seconds of sitting at the logon screen, the second just starts.

```
james@monkey:~$ uptime
 16:05:39 up  2:04,  3 users,  load average: 3.80, 2.10, 1.70
```

I've got two terminals open and I'm logged into this instance of Xorg. I'm not logged into the other one, it just runs.

---

### Post by encompass on 2006-09-08
Looks like something you did... I am sorry but I haven't a clue how to stop it.  Do you remember ever doing something with autologin or anything of the like?

---

### Post by lozenge on 2006-09-08
Regardless of autologin, it's two instances of Xorg, nothing is logging in anywhere.

It started happening after my computer lost power. I started it back up and two Xorgs started.

I have not changed any essential parts of the system.

---

### Post by Ramses de Norre on 2006-09-08
```
gksudo gdmsetup
```
Security tab, in the right hand bottom corner click "Configure X Server..." and make sure you only have one server to be started in the column at the left (I have VT:0; Server: Standard; Options: none (white)).

---

