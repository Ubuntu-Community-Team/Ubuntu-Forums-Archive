---
title: "Can't run a app on a X server"
date: 2007-01-18
forum: Desktop Environments
---

### Post by snowboard975 on 2007-01-18
I used telnet to connect to a X server.
Everything worked fine until I tried to run a application with GUI.

```

forest@forest-computer:~$ telnet 163.***.**.**
Trying 163.***.**.**...
Connected to 163.***.**.**.
Escape character is '^]'.
Red Hat Linux release 8.0 (Psyche)
Kernel 2.4.18-14 on an i686
login: A19
Password: 
Last login: Fri Jan 19 09:46:58 from 163.***.**.***
[A19@kilby05 A19]$ cd opus
[A19@kilby05 opus]$ icfb &
[1] 29356
[A19@kilby05 opus]$ *ERROR* X Window Display Initialization failure
*WARNING* X Window Display Initialization failure

[1]+  Exit 255                icfb
[A19@kilby05 opus]$ 

```

I would run the icfb program on a windows XP through Exceed by Hummingbird, but I can't do it now on Ubuntu. What can I do to solve this problem?

---

### Post by IamAcoconut on 2007-01-20
Why don't you try using ssh with '-X' option?

---

### Post by snowboard975 on 2007-01-21
Thanks a million!!
The following code solved problem!!!
```
ssh -X myuserID@163.***.***.*** 
```

How foolish I am! Actually I saw your thread before, but I couldn't realize this simple method would solve my problem.

---

### Post by IamAcoconut on 2007-01-22
I'm glad I could help :)

---

