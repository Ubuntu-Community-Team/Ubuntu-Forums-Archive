---
title: "Big problem!!!"
date: 2008-08-27
forum: Desktop Environments
---

### Post by Professore on 2008-08-27
I have a prolem with ubuntu. Every time I try to install things i get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What can i do for this? Is there a permanent solution???

---

### Post by DavidTangye on 2008-08-27
What version are you running? Run ```
uname -r
``` and post the result.

---

### Post by Professore on 2008-08-27
2.6.24-19-generic

---

### Post by DavidTangye on 2008-08-27
OK. Reboot and boot into 'Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)'.

 - At the screen that appears select the third option: 'root Drop to root shell prompt'.
 - Run the command ```
dpkg --configure -a
```. Then exit or Ctrl-d to get out.
 - Select the top option now: 'resume' to continue with a normal boot, and all should be ok.

---

### Post by Professore on 2008-08-27
I did it but when i typed the dpkg thing i got some other options. I tried it but it has no effect

---

### Post by Professore on 2008-08-27
Can i do sth else? Maybe someone can help??

---

### Post by DavidTangye on 2008-08-27
> **Professore said:**
> Can i do sth else? Maybe someone can help??No :-).

Post the output of the dpkg command. To capture it run dpkg --configure -a|tee dpkg.log
Then you can attach dpkg.log to a post here after you have resumed to a normal boot, as before.

---

### Post by Professore on 2008-08-27
ok. ill try it a bit later cause im busy!!

---

### Post by The Shadow on 2008-09-14
I am having the same problem. I ran "dpkg --configure -a" but it never completed. It hung up at 

"invoke -rc.d:initscript dbus, action "force-reload" failed"
*Starting Hardware abstraction layer hals

It did however upgrade my system from kernel 2.6.17-12 to kernel 2.6.20-16.

any suggestions?

---

### Post by wilcan34 on 2008-09-17
Am having same prob. Sownloaded 8.10 and get the same mess.E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
Will try Dave T's Idea.
Will do now and let you Know outcome.
Regards
G

---

