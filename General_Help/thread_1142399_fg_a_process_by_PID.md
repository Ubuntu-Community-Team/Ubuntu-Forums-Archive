---
title: "fg a process by PID"
date: 2009-04-29
forum: General Help
---

### Post by PeterVR on 2009-04-29
I'm running a long time process, initiated in a past ssh session. I can see the process running, I can see its PID, but there's no way I can bring it back to foreground.

The fg command doesn't work with PIDs, it uses temporary session-owned ID's. 

Demo:
```
petervr@belenos:~$ sleep 8000000

[1]+  Stopped                 sleep 8000000
petervr@belenos:~$ bg 1
[1]+ sleep 8000000 &
petervr@belenos:~$ ps
  PID TTY          TIME CMD
18189 pts/1    00:00:00 bash
18273 pts/1    00:00:00 sleep
18274 pts/1    00:00:00 ps
petervr@belenos:~$ jobs
[1]+  Running                 sleep 8000000 &
petervr@belenos:~$ fg 18273
-bash: fg: 18273: no such job
petervr@belenos:~$ fg 1
sleep 8000000


```

Now when I start a new SSH session, how can I get the sleep process to foreground?

```
petervr@belenos:~$ ps
  PID TTY          TIME CMD
18278 pts/0    00:00:00 bash
18297 pts/0    00:00:00 ps
petervr@belenos:~$ ps -u petervr
  PID TTY          TIME CMD
18188 ?        00:00:00 sshd
18189 pts/1    00:00:00 bash
18273 pts/1    00:00:00 sleep
18277 ?        00:00:00 sshd
18278 pts/0    00:00:00 bash
18298 pts/0    00:00:00 ps
petervr@belenos:~$ fg 18273
-bash: fg: 18273: no such job
petervr@belenos:~$ fg 1
-bash: fg: 1: no such job
petervr@belenos:~$
```

---

### Post by Brandon Williams on 2009-04-29
There is no way that you can foreground a process in your current shell instance if it was not started in your current shell instance. You can't take over a process that was started in a different shell.

There are programs available that allow you to move other programs around from one shell instance to another, the most common one is screen. If you didn't start your long running process inside of a screen session, then you won't be able to do what you want to do.

---

### Post by slakkie on 2009-04-29
What he said ^^^^

---

### Post by kpkeerthi on 2009-04-29
[screen]("https://help.ubuntu.com/community/Screen") might help

---

### Post by spacedoubtman on 2013-03-24
this is an old question but the first result on google when I searched for "fg a process by PID" and not very helpful answers

you can send the SIGCONT signal to resume a suspended process - you don't have the input redirected to your shell as per fg but it is resumed which is what I believe the op was asking

use the kill command to do this eg.
kill -SIGCONT 8679

---

### Post by oldos2er on 2013-03-24
Old thread closed.

---

