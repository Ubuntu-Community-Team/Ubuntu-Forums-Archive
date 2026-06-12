---
title: "GDM PostLogin script doesn't start in Karmik"
date: 2009-11-11
forum: Desktop Environments
---

### Post by mitsui on 2009-11-11
Hi,
   I have a problem with karmik: the /etc/gdm/PostLogin/Default script doesn't start. I've used it since Hardy (to Jaunty) without any problem.. Anyone know what's the difference in this script with older Ubuntu?
Thanks!

---

### Post by deadite66 on 2009-11-13
just hit this problem too.

---

### Post by mitsui on 2009-11-13
Thanks!
There's any fix for it?

---

### Post by LordNils on 2009-12-12
I just ran into this problem too and it seems like PostLogin/Default has some different behavior now. The script is started if i disable the Autologin, which was enabled before because i got an encrypted /home which is beeing decrypted in PostLogin/Default.

If that doesn't work, a different approach is explained here: [http://ubuntuforums.org/showthread.php?t=1014891](http://ubuntuforums.org/showthread.php?t=1014891)
(edit /etc/gdm/Init/Default so it starts your script before your login)

Perhaps it helps anyone...
nils

---

