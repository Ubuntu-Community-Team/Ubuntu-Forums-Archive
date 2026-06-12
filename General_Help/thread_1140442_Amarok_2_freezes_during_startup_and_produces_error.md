---
title: "Amarok 2 freezes during startup and produces error message in terminal"
date: 2009-04-27
forum: General Help
---

### Post by diablo75 on 2009-04-27
I'm running Ubuntu 9.04 (fresh install on a HP Compaq 6715b laptop).

So when I start Amarok, the new splash screen appears while you think it's loading up, but it just stays there forever and never seems to go away.  Amarok never successfully loads; just this splash screen.  So I did a "sudo apt-get purge amarok" followed by "sudo apt-get install amarok" in terminal, then attempted to run it using the command "amarok" in terminal.  The splash screen loads as usual, and in the terminal there is one line of output:

```
amarok(3968) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
```

Then the command prompt returns to your file system, like you'd expect it to when a program crashes, but the splash screen is still stuck.  Running a "killall amarok" in terminal will kill the splash screen.

So I don't know what to make of this.  Am I missing a package perhaps?

---

### Post by Brandma on 2009-07-16
I'm pretty sure I have the same problem.  Here's what I get when I try to run Amarok in Terminal:

matt@brandma:~$ amarok
amarok(9301) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
<unknown program name>(9300)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

matt@brandma:~$

---

### Post by perrti-y02 on 2009-07-16
Are you running anything like Xine (movie player) at the same time?
Do you have Xine installed?

---

### Post by Brandma on 2009-07-16
No other programs like Xine running, and I found out I didn't have it installed.  I installed it with 'sudo apt-get install xine-ui' as terminal suggested, but when I tried to load Amarok after that, I got the same error.

---

### Post by perrti-y02 on 2009-07-16
I would try completely removing Amarok and reinstalling. It might pick up loose ends and correct this error.

---

### Post by Brandma on 2009-07-16
Still didn't work.  I did 'sudo apt-get purge amarok' (because a simple remove didn't work in the past), shut down the computer, turned it back on, installed Amarok, and I still get the same problems/error.

---

