---
title: "cant login anymore, need help"
date: 2009-01-21
forum: General Help
---

### Post by kobayashimaru on 2009-01-21
Hello,

i have a strange problem and cannot write much at the moment. gdm and login crash while logging in. login in recovery mode successfull. /var/log/messages. says segfault in pam_smbpass.so for both gdm and login programs

could anyone please help me? thx

---

### Post by gjoellee on 2009-01-21
> **kobayashimaru said:**
> Hello,

i have a strange problem and cannot write much at the moment. gdm and login crash while logging in. login in recovery mode successfull. /var/log/messages. says segfault in pam_smbpass.so for both gdm and login programs

could anyone please help me? thx

Can you launch GDM from terminal? ```
gdm
```you might have to use : ```
sudo gdm
```?

If not I found a bugreport for this. It is related to PAM. Maybe this will work: ```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get reinstall pam
```

---

### Post by kobayashimaru on 2009-01-21
more information.. I cannot not login as any user. In recovery mode I can login as root.
I have not changed anything to my system in the last days. was working yesterday. I dont have a clue whats going on here. sad that i cannot upload screenshot of logfile here.

---

### Post by kobayashimaru on 2009-01-21
Thank you for your help gjoellee,

My system is working again.
Your instruction to reinstall pam seems to be outdated, since pam is not an installable package. But instead I removed libpam-smbpass. That did the trick, because this was the "bad" library.
Now I wonder why I had this library and why it caused an error. Maybe I will never find out ;-).
For me this problem is solved.

---

