---
title: "Ubuntu 9.04 shuts down and freezes often"
date: 2009-05-05
forum: General Help
---

### Post by boki_hp on 2009-05-05
Alright I'm new in Ubuntu, linux ... I've installed Ubuntu 9.04 and the needed programs made the updates that were in the update manager and the very next day the system shuts down I mean a black screen appears the computer works but ubuntu no, I wait a while and I restart the computer. After that a hour or two i work normally in firefox and then ubuntu freezes i wait about 5 minutes and nothing happens and I restart the computer. The next day once again ubuntu shuts down and after that freezes a few times. And now I'm writing here. It's not my first time to install ubuntu I've installed 8.10 before. I also have win xp installed. Oh and i didn't install the ati driver in ubuntu because in 8.10 I've had several problems with it and I've decided not to install it cause it worked perfectly without it. 
If someone knows what is the problem and how to fix ?
Thanks in advance.

---

### Post by decoherence on 2009-05-05
I'll assume you don't have this problem in Windows.

Wild guess: your power management isn't working properly and your computer is overheating. Does it run very hot?

---

### Post by boki_hp on 2009-05-05
Nope windows works fine. And it doesn't run 'hot' it runs normally. If it's the power management on the computer windows should have similar problems. Any other guess :p

---

### Post by miked2 on 2009-05-05
Have you tried looking through the system logs?  There might be some clues there.  
System - Administration - Log File Viewer.

---

### Post by decoherence on 2009-05-05
> **boki_hp said:**
>  If it's the power management on the computer windows should have similar problems.

Nope. They are different power management systems. Certain hardware is better supported under linux than others. That said, if it isn't running hot then that probably isn't the problem.

At this point I'm with miked2. Hopefully there's something in the logs. Just note the time at which the problems occur and use that to figure out where in the log to look (the time of the problem and a little while before)

---

### Post by roberthr on 2009-05-05
Jaunty seems to have lockup problems and no solution yet:
[http://ubuntuforums.org/showthread.php?p=7220128#post7220128](http://ubuntuforums.org/showthread.php?p=7220128#post7220128)

---

### Post by boki_hp on 2009-05-05
I found those syslog messages ok I get the freezing but what about the shuting down. A few minutes ago it happened again I looked in the syslogs and found nothing.

---

### Post by boki_hp on 2009-05-05
what about i post a part of the syslog and you guys can figure it out.

---

### Post by boki_hp on 2009-05-05
I had to post it in a zip file the txt was too big

---

### Post by boki_hp on 2009-05-05
anyone :(

---

### Post by Nrok on 2009-05-18
Having the same problem on my HP Compaq 8710w... Also new to Ubuntu, just wanted to give it a try since everybody is saying linux is much better... more secure, more stable etc...
 
I gotta admit that the way you can grab and install software is just sweet, keeping your system up-to-date and secure is so easy. The only thing I dislike sa far are the freezes. The system completely hangs ... in Vista or XP I can go to the taskmanager and kill the process, on my system Ubuntu isn't able to present me with the taskmanager upon pressing alt f2 etc.
 
To bad :( ... I really liked it so far. Switching to the current LTS to see if that helps.
 
Ubuntu is the only OS installed and got the full disk to work with, didn't install things that are not avaible from the default packet management "channel".

---

### Post by Nrok on 2009-05-19
It's me again with an update.

Installed the current LTS Ubuntu 8.0.4 and works like a charm... no freezes... So I will continu to explore the OS a bit more ... this enjoying it without the freeze :P

---

