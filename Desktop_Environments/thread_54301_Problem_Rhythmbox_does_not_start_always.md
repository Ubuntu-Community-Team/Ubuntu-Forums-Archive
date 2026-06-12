---
title: "Problem: Rhythmbox does not start always"
date: 2005-08-04
forum: Desktop Environments
---

### Post by tom-ubuntu on 2005-08-04
Hi all

Got a strange problem with Rhythmbox: When I like to start it, it does not apear on the screen. But when I check the processes (ps aux) It is listed there. I sometimes start it then several times, just to test, and the same happens: does not apear on the screen, but process is started. Killing the processes is also not possible.

Any ideas? Or better: solutions? ;)

Thanks in advance
Joe

---

### Post by heimo on 2005-08-04
Not really a solution, but a way to debug. Open it from terminal window (Applications->System Tools->Terminal)  type rhythmbox [enter]

This way you may get some error messages. To kill the process, try *killall rhythmbox *or *kill -9 pid *where pid is process id (list of processes *ps aux* *| less*)

---

