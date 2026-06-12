---
title: "problem"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Abadon on 2006-07-20
Hi there,

I'm really new with linux. I just installed  32 bit version of Drake and configured the firefox so all the plugins such as java and micromedia flashplayer work correctly. My problem started when I just tried to install anything from add/remove or Synaptic package Manager.The message pops out saying: **E: dpkg was interrupted, you must manually run'dpkg--configure-a' to **correct the problem. If anyone knows how to fix this please let me know.

---

### Post by philippe_carlo on 2006-07-20
> **Abadon said:**
> Hi there,

I'm really new with linux. I just installed  32 bit version of Drake and configured the firefox so all the plugins such as java and micromedia flashplayer work correctly. My problem started when I just tried to install anything from add/remove or Synaptic package Manager.The message pops out saying: **E: dpkg was interrupted, you must manually run'dpkg--configure-a' to **correct the problem. If anyone knows how to fix this please let me know.

Do the following at the terminal and post the output here.
```
sudo apt-get install -f
```

---

### Post by Abadon on 2006-07-20
Hi Philippe_Carlo

I run this command in terminal- sudo apt-get install -f
 and got the same message:**E: dpkg was interrupted, you must manually run** **'dpkg --configure -a' to correct the problem.** I really hope there is some kind of solution to this problem so I don't have to reinstall ubuntu.

---

### Post by Ramses de Norre on 2006-07-20
Did you allready try to run ```
sudo dpkg --configure -a
``` as suggested?

---

### Post by Abadon on 2006-07-20
Thanks it looks like my micromedia flashplayer was cousing all this. I removed it using synaptec and everything looks good. Does anyone know what's the best way to get flash player installed.  Thanks again

---

### Post by bulldog on 2006-07-20
I used Automatix to install flashplayer and a lot more apps.
There is a topic about Automatix on this forum.
Just see wat it can do for you.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

---

