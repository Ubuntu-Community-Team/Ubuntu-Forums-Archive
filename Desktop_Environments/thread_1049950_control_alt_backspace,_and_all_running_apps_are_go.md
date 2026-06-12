---
title: "control alt backspace, and all running apps are gone .."
date: 2009-01-25
forum: Desktop Environments
---

### Post by bosworthy on 2009-01-25
Q1

control alt backspace, and all running apps are gone after i log back into genome.  i run ps -ef and i do see the process running.  I tried to open as many programs as I can to test my swap configuration via free.


Q2

Is it okay to hit control alt backspace then when I get the prompt, i type shutdown?  linux won't shutdown when i hit the shutdown icon when I have all sorts of application running (nothing is important..was just testing).

I'm surprised that I don't have to be root to shutdown / reboot linux.  if i were to remote into my computer, would i be able to shutdown?  i haven't gotten that far yet..  i installed the server edition of ubuntu 8.04 and i was really surprised it would let me type the shutdown command. 

Q3

Is there something I can do to log of genome into pure shell ..  is it SAFE to open a prompt and type something to get me into single user mode within genome?

Thanks.

---

### Post by ugm6hr on 2009-01-25
I'm afraid I don't fully understand what you are asking.

But Ctrl-Alt-Backspace is not recommended, since it just shuts down X server.

If you want to get to a Terminal, try Ctrl-Alt-F1 (or F2).

shutdown, reboot, poweroff generally require sudo privileges.

---

### Post by bosworthy on 2009-01-25
Well, can you verify if hitting control, alt, backspace, then it'll drop you to a shell prompt, from there, type shutdown, and see if it'll bring your machine down?  This is what I see on 8.04 server edition :)  I think it is assumed this is possible because if person is in front of the box, he/she can simply pull the power cord to have the same effect, so in a way, this isn't a security risk.  I don't know if above is allowable if I were to remote in.  Currently , I don't know how to remote into my machine yet :)  learning.

do you know how I can get those apps back though if I were to type startx and it's not there? Is this even possible?  thanks.

If you can tell me which part needs clarification, I'd be glad to provide. :)

I just figured out control alt f7 brings me back to gui. phew.

---

### Post by Shazaam on 2009-01-25
Simple shutdown code...
```
sudo shutdown -h now
```
-h means halt at the end of the shutdown run; now means now, not later.
To get a better idea about the shutdown command enter this in terminal...
```
man shutdown
```
(man stands for manual)

---

### Post by bosworthy on 2009-01-29
is it safe to do a sudo shutdown while I'm inside Genome w/ a shell prompt?  Or do I need to somehow get out of and shutdown genome first, which I don't know how to do at this point.

Thanks.

> **Shazaam said:**
> Simple shutdown code...
```
sudo shutdown -h now
```
-h means halt at the end of the shutdown run; now means now, not later.
To get a better idea about the shutdown command enter this in terminal...
```
man shutdown
```
(man stands for manual)

---

### Post by sedawk on 2009-01-29
Pressing Ctrl+Alt+Backspace kills your complete Desktop, the
X-Server (the process responsible for "painting the graphics") will
stop and so will all processes that are running on the desktop.

When you run shutdown there is a bunch of shutdown scripts that
is executed in a well defined sequence. One of these scripts
will also shutdown the desktop, so you can run shutdown from
within the desktop.

For checking swap activity have a look at the command line tool "vmstat".

The default user of Ubuntu is in group "admin", so he can do some
things normal users cannot do, e.g. a normal user can only logout from
Desktop but not shutdown the whole machine.

---

