---
title: "Natty wake up to black screen"
date: 2011-04-30
forum: Desktop Environments
---

### Post by yotama9 on 2011-04-30
Hi guys.

I have install Ubuntu Natty on two different machines. One of them a laptop (Thinkpad edge 13'') which was upgraded from Ubuntu Mavrik. The other is a desktop machine which has opensuse previously installed.

On the laptop, when I close the lead, and open it again I get a black screen only with the mouse pointer visible (and moving) but without any response. 
On the desktop, when the screen wakes up, I get the same issue (black screen with pointer and so on). The desktop is still streaming music in this mode. 

Both machine have intel display card installed on them. 

How can I fix this?

Thanks.

---

### Post by yotama9 on 2011-04-30
Solved, kinda:

sudo pkill X

[http://ubuntuforums.org/showthread.php?p=10742430](http://ubuntuforums.org/showthread.php?p=10742430)

---

### Post by pmh1wheel on 2011-05-07
I've seen the same problem at least twice on my laptop, and can give slightly more detail, but no solution yet.

On waking the laptop, the system comes back running everything, but the only sign of X is the mouse cursor. I can tell that the desktop is still active, because the cursor changes according to whatever it's hovering over, and if I know where my terminal window is, I can type commands into it which get executed successfully. I can successfully switch to text consoles with Ctrl-Alt-Fn, and even to other X sessions, which seem to work perfectly.

The only console which doesn't display anything is the one which was showing when the screen was powered down. More than that, it doesn't even seem to try to display anthing other than the mouse cursor, leaving the previously active console still visible after switching.

---

### Post by rha1063 on 2011-08-17
I have the same problem. Natty installed via Wubi on my Dell Vostro V13. Same behavior -- black screen on wakeup, mouse cursor moves and changes shape. CTRL-ALT-F1 works.

---

