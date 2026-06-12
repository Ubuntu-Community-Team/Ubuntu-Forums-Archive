---
title: "[help] can't switch user"
date: 2008-05-03
forum: Desktop Environments
---

### Post by benquick on 2008-05-03
Hi all, i had a problem with ubuntu 8.04 32 bit edition, i can't switch or login with any other user, every time i switching (fast user switching) or logging in to any other user, my computer always logged back to default user (user that i create when installation), i try to reinstalling system but i got same problem, anyone help me please.. to resolving my computer trouble

i trying to install hardy on the other computer and everything's gonna be okay

---

### Post by Patb on 2008-05-03
Ben, have you actually created those other users?  What is the output of:
```
ls /home/
```
Also, could you please start switch user from a terminal:
```
gdmflexiserver
```
That should put you through the switch user process.  Log back as yourself and if there is any error output from that shown in the terminal, please post it.  

Cheers, Pat.

---

### Post by benquick on 2008-05-03
Thank's patb, i did your suggestions, and here the result:
> bokura4@bokura4:~$ ls /home/
[COLOR="Purple"]bokura4[/COLOR]  [COLOR="DarkOrchid"]ws4[/COLOR]


> bokura4@bokura4:~$ gdmflexiserver
bokura4@bokura4:~$ 

as you see, no error messege on terminal after logging back
any suggestion?

---

### Post by Patb on 2008-05-03
Ben, that looks okay.  

Can you log on as ws4 directly from a normal boot?  Your original post indicates that if you try, it logs you in as bokura4.  Is that what happens?  

Also, could you post the output of:
```
cat /etc/passwd | grep "/home"
```

Terima kasih, Pat.

---

### Post by benquick on 2008-05-04
```

Can you log on as ws4 directly from a normal boot?

```
No, i can't log on as ws4 directly from a normal boot, i only can log onto bokura4, and this is output of cat /etc/passwd | grep "/home"
```

bokura4@bokura4:~$ cat /etc/passwd | grep "/home"
syslog:x:102:103::/home/syslog:/bin/false
klog:x:103:104::/home/klog:/bin/false
bokura4:x:1000:1000:bokura4,,,:/home/bokura4:/bin/bash
ws4:x:1001:1001:ws4,,,,:/home/ws4:/bin/bash
bokura4@bokura4:~$ 

```

> 
Terima kasih, Pat.

sama-sama, ben.

---

### Post by Patb on 2008-05-04
Ben, thanks for the information.  

It seems that you have just two users, bokura4 and ws4, and that for some reason ws4 is not being accepted as a legitimate user.  At this stage, I would create a new user from a terminal: 
```
sudo adduser <your_new_user_name>
```
and then log in as bokura4 and try to switch to that user.  If that works, you could either try to re-add ws4 as a "legitimate" user:
```
sudo adduser ws4
```
or delete user ws4 (back up any useful files in /home/ws4/ first just in case):
```
sudo deluser ws4
```

If that works, please mark the thread as solved.  

Terima kasih, Pat :)

---

### Post by benquick on 2008-05-04
patb, thanks for quick reply

it doesn't work, i try to add new user from a terminal
```
 sudo adduser client4 
``` and then, i try to switch to client4 user, same like before, switch back to bokura4 user.
i know this not too important, coz i can use bokura4 user, but i guess... this a unique problem, i was reinstalling system for twice, should i reinstalling again?:confused:
when use a gutsy, i never found this trouble, but i like hardy, coz fast installation and more stable.
patb, sorry if i fussing you, thank you very much :)

---

### Post by Patb on 2008-05-05
Ben, sorry but I am running out of ideas now.  What you have done should have worked okay.  I am lost as to what the problem is.  If you have already installed twice, I doubt that a reinstall will do any good.  

One thing I would like to check is permissions for each user.  Could you please leave your new "client4" user there (or recreate it) and then post the output of;
```
ls -ld /home/*
```
> **benquick said:**
> sorry if i fussing you, thank you very much :)

Tidak masalah Pak.  Saya senang menolong. Tetapi maaf, Bahasa Indonesia saya fairly rough. :)

Cheers, Pat.

---

### Post by benquick on 2008-05-05
Here the output of:
```

bokura4@bokura4:~$ ls -ld /home/*
drwxr-xr-x 42 bokura4 bokura4 4096 2008-05-05 13:22 /home/bokura4
drwxr-xr-x 20 client4 client4 4096 2008-05-05 10:44 /home/client4
drwxr-xr-x 20 ws4     ws4     4096 2008-05-04 14:46 /home/ws4

```
:KS Terima kasih banyak

---

### Post by Patb on 2008-05-05
Ben, that latest output looks fine.  It is quite consistent with what I get on my system.  From all you have posted I cannot see any reason for your problem.  Sorry but I cannot think of anything else.  I hope someone more expert can help. 

Cheers, Pat.

---

### Post by benquick on 2008-05-05
Patb, thanks for your attention, no matter if my problem can't resolved, coz I can use the default user, i only wondering why I can't switch user, thats all.
\\:D/ cheers, Ben.

---

### Post by benquick on 2008-05-10
now after i check, check and recheck again, i know this problem happen after i installing vga driver (via), but i don't know why this problem happen on this computer, and the other computer (with the same hardware specification), everythings gonna be okay, hmmmm....:confused::confused::confused::confused::confused::confused::confused::confused:

---

