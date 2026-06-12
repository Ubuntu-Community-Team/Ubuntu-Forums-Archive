---
title: "Init.d startup script help... please."
date: 2005-09-18
forum: Desktop Environments
---

### Post by basse1989 on 2005-09-18
Hello everyone.

I want to create a script that starts my hlds server (half-life) and runs my iptables script.
I want it to make a detached screen named hlds (using screen -S hlds) for the half-life server so I can check in on it.
But so far I haven't been able to make a script that starts the hlds server in a screen and DON'T show the screen.

I only want it to say "Staring scripts" or something, not switch to the hlds screen and mess up everything....

Can someone please help me?

---

### Post by Zwack on 2005-09-19
from man screen

...
       -d -m   Start screen in "detached" mode. This creates a new session but
               doesn’t  attach  to  it.  This  is  useful  for  system startup
               scripts.
...

So, while I'm not a screen expert, in your start section you want to do...

screen -d -m -S hlds <server command>

I tried this with 

screen -d -m -S hlds vi

and I end up with a vi running in pts/1
$ screen -d -m -S hlds vi
$ ps -elf | grep vi
1 S user     6632     1  0  76   0 -   997 -      20:59 ?        00:00:00 SCREEN -d -m -S hlds vi
0 S user     6633  6632  0  76   0 -  1282 -      20:59 pts/1    00:00:00 vi
0 R user     6640  6524  0  78   0 -   726 -      20:59 pts/0    00:00:00 grep vi
$ 

No message, no nothing...

I hope that this helps,

Z.

---

### Post by basse1989 on 2005-09-19
Me happy. :)

Thanks. :)

---

### Post by Zwack on 2005-09-20
No Problem, I'm glad I could be of assistance...

Z.

---

### Post by misse- on 2005-12-16
[QUOTE=Zwack]from man screen

...
       -d -m   Start screen in "detached" mode. This creates a new session but
               doesn’t  attach  to  it.  This  is  useful  for  system startup
               scripts.
...

So, while I'm not a screen expert, in your start section you want to do...

screen -d -m -S hlds <server command>

I tried this with 

screen -d -m -S hlds vi

and I end up with a vi running in pts/1
$ screen -d -m -S hlds vi
$ ps -elf | grep vi
1 S user     6632     1  0  76   0 -   997 -      20:59 ?        00:00:00 SCREEN -d -m -S hlds vi
0 S user     6633  6632  0  76   0 -  1282 -      20:59 pts/1    00:00:00 vi
0 R user     6640  6524  0  78   0 -   726 -      20:59 pts/0    00:00:00 grep vi
$ 

No message, no nothing...

I hope that this helps,

Z.[/QUOTE]

Since I do not know squat about putting lines in init.d, or anything about autostarting in linux or ubuntu. So, how to make my hlds start automaticly when booting ubuntu, server installation?

---

### Post by TTrane on 2008-03-28
> **misse- said:**
> Since I do not know squat about putting lines in init.d, or anything about autostarting in linux or ubuntu. So, how to make my hlds start automaticly when booting ubuntu, server installation?

To make the HLDS run at linux boot, just add the start-up command (with or without screen) to the /etc/rc.d/rc.local file. For example (using screen):

# echo "cd /usr/hlds" >> /etc/rc.d/rc.local
# echo "screen -A -m -d -S hlds ./hlds_run -game cstrike -autoupdate +maxplayers 20 +map de_dust2" >> /etc/rc.d/rc.local

---

