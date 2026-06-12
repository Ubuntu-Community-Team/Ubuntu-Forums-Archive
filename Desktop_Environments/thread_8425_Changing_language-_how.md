---
title: "Changing language- how?"
date: 2004-12-17
forum: Desktop Environments
---

### Post by deiniol on 2004-12-17
Hello,

Looking over FAQs and HOWTOs, it seems that to change the interface language you have to run *sudo dpkp-reconfigure locales*, but when I type that into a terminal I get *bash: dpkp-reconfigure: command not found*. Am I doing something wrong? :???:

---

### Post by Rui Pais on 2004-12-17
Hi, probabilly thats because dpkg-reconfigure is in /usr/sbin/ (not /usr/bin/) so you have to su first and then, as root, do dpkg-reconfigure. 
It happens to me, too... and is boring, because root, by default in Ubuntu don't have a password! You will have to give that danger guy a password or add /usr/sbin to your path. 
I done both, to avoid more pains.

Why Ubuntu insist on sudo-only approach by default and leave /sbins out of touch is a mistery to me...

hope this help you

---

### Post by p!=f on 2004-12-17
I think it's just a typo, right?
> 
dpkp-reconfigure: command not found

You don't need to su. I don't recommend it. If you want root profile, run this
```

sudo -s

```
You won't need to setup root's password.
```

sudo dpkg-reconfigure locales

```
should be sufficient.

---

### Post by Rui Pais on 2004-12-17
You are right, of course. 
I assumed it was not a typo. The same thing happen to me, just because /sbin and /usr/sbin are not in my PATH. So sudo dpkg-reconfigure just give a not found error. My point it was only add those paths to PATH variable or make sudo /usr/sbin/dpkg-rec... wich is boring, of corse (One distro didn't even allow me to reboot by typing only reboot... it was debian? I can't remeber)

Sudo is always the right choice, i agree 110%, but keep root without a password may prevent users to login as root... but can't prevent an naif user to do (DON'T DO IT) sudo nautilus... Security must start at peoples knowledge, i think... hiding stuff or block actions will usually just irritate users and let them think of that as system limitations...

---

### Post by deiniol on 2004-12-17
Umm. It was a typo.   *Twpsyn ydw i.* 8-[

---

