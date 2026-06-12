---
title: "Default behavior when gnome fails to start"
date: 2009-01-29
forum: Desktop Environments
---

### Post by ridetheteapot on 2009-01-29
By default if gnome is having display trouble and can't start it gives you 3 options in a gtk window. check the logs, restart gnome in low res graphics, and something else. If (when) this happenes I never use any of those options, all i want to do is kill gdm. First i must choose restart in low graphics mode before i can stop gdm.
I was wondering if there is a way to get gnome to just stop itself rather than giving me those choices.

---

### Post by Yashiro on 2009-02-07
Press Ctrl+Alt+F1. Log in and do /etc/init.d gdm stop
Your Gui session is on Ctrl+Alt+F7 still.

---

### Post by ridetheteapot on 2009-02-15
My point being exactly that.

First off, if you want to stop the gdm first you need to start it. (you MUST choose to start in low res mode before you stop the gdm)

What i am asking about is that is there a way to stop the prompt for low res mode if gdm has trouble starting.

(If you dont start gdm before you kill it in tty then you will get a new gdm on a different tty or it will just fail because 7 is taken by the broken gdm)

---

### Post by Yashiro on 2009-02-15
Yes. You could stop it launching I guess.
You'd have to mess with /etc/rc.d and stop gdm from starting up (or just chmod -x to the gdm init). Not sure if this will break alot of things though.

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)
[http://www.linux.com/articles/114107](http://www.linux.com/articles/114107)

Probably better to resolve why you're having these crash issues.

---

### Post by ridetheteapot on 2009-02-15
thanks for the info Yashiro 
gdm is already not set to start boot, but i'm wondering if you can change how it acts when if fails (even when you start it manually). I will keep looking into it cause I think there is a way.

sometimes i am experimenting with different oss gfx driver forks (and different cards) and have to compile them, gets annoying after a few misfires.

------------
Marked As Solved

Ubuntu has new options when gnome fails that makes this nice and smooth

---

