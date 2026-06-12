---
title: "Installing VNC software on Xubuntu"
date: 2008-05-18
forum: Desktop Environments
---

### Post by armitage1337 on 2008-05-18
Hi,

I'm trying to replicate Ubuntu's VNC server setup on Xubuntu, but I've had no luck so far. I've searched these forums, and tried installing Vino, but nothing has worked for me. When I try to connect, the VNC client hangs every time after I enter the password. Moreover, I have to manually start vino-server with ```
/usr/lib/vino/vino-server
``` Any ideas on how to get the exact same setup (connect, and it shows the current logged in user's screen)?

Thanks in advance for the help!!

---

### Post by nycjeff on 2008-07-06
I think I'm having a similar problem.
I've set up vino on my ubuntu machne and I can connect to that one.
When I set up vino on my xubuntu machine, I've got a problem.
It doesn't show up in the processes section of System Monitor so I don't even think its running. 
Just wondering if anyone else has had a similar problem with vino and xubuntu.
-jeff

---

### Post by nycjeff on 2008-07-06
This thread solved my problem.
[http://ubuntuforums.org/showthread.php?t=726789](http://ubuntuforums.org/showthread.php?t=726789)

---

### Post by pedor on 2008-07-17
vino don´t work for me  either 
I run /usr/lib/vino/vino-server but get only Connection refused  when i try to connect.

---

### Post by nycjeff on 2008-08-04
pedor,
did you run "vino-preferences" at the command line first?

---

