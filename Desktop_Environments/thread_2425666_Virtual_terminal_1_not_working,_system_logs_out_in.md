---
title: "Virtual terminal 1 not working, system logs out instead"
date: 2019-08-28
forum: Desktop Environments
---

### Post by toxup on 2019-08-28
5.0.0-25-generic #26~18.04.1-Ubuntu SMP Thu Aug 1 13:51:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

I have this problem on both my stationary and Thinkpad laptop. Going to virtual terminal 1 by pressing ctrl+alt+F1 or entering chvt 1 will simply log me out of the system and I'll end up at the login prompt. VT 3 works, but none of the others. ctrl+alt+F7 will not return me go GUI either.

Another symptom: I have to log in twice, i.e. only the 2nd time I enter my login password will I actually log in. The screen flashes after the 1st time and I return to the login screen.

Any advice on where to start?

Thanks!

---

### Post by cruzer001 on 2019-08-28
Please post the output of:
```
echo $DESKTOP_SESSION && echo $DESKTOP_TYPE && sudo apt -f install
```

---

### Post by cruzer001 on 2019-08-28
Came across this.

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1758512](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1758512)

---

### Post by toxup on 2019-09-03
The 1758512 bug is not identical as tty3 and above works well, but tty2 and 1 will not appear and the system simply gives me the login screen.
my Desktop session and type is regolith.

 tty2 will not do anything from the regular desktop session, but will give me the login screen if I attempt to enter it from tty3. tty1 will give me the same login screen both from the regular desktop session and a virtual terminal. 
New observation:
As I said, at the login screen I have to enter the credentials twice. The first time there is no "settings wheel" where I can choose the desktop session. This is only present at the second time and here I can choose between
Regolith
Ubuntu with wayward
Ubuntu

---

