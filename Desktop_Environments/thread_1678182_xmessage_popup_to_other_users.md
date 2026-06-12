---
title: "xmessage popup to other users"
date: 2011-01-29
forum: Desktop Environments
---

### Post by Bynw on 2011-01-29
I am wanting to send a popup message to another user logged on the system. They would be using the GUI (GNOME) desktop while I would be at a remote location and SSH'ed into the box.

using w
I am able to see they are on display :1

So I attempt to use xmessage (or gxmessage both are installed) and this is what happens:

chris@outlaw:~$ xmessage -display :1 -center "hi"
No protocol specified
Error: Can't open display: :1


I know there has to be a way that as a sudoer I can send the message to their display but as of yet I have not been able to discover it on my own. Any help would be appreciated. 

Thank you.

---

### Post by Cheesehead on 2011-01-30
Try:
```
DISPLAY=:1 xmessage -center "hi"
```

---

### Post by Bynw on 2011-01-30
Unfortunately that did not work either.

```


chris@outlaw:~$ w
 20:59:25 up 2 days,  3:32,  3 users,  load average: 0.57, 0.45, 0.33
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
chris    tty7     :0               Fri17    2days  5:00m  2.98s gnome-session
chris    pts/0    173-25-*-*.c     20:59    0.00s  0.65s  0.01s w
kristen  tty9     :2               16:54    2days  4:31   0.24s gnome-session
chris@outlaw:~$ DISPLAY=:2 xmessage -center "Testing, one two and three!"
DISPLAY=:2 xmessage -center "Testing, one two and three"
No protocol specified
Error: Can't open display: :2


```

---

### Post by discodex on 2011-11-21
This may be a permissions issue. You may have to run:

sudo DISPLAY=:2 xmessage -center "Testing, one two and three!"

---

