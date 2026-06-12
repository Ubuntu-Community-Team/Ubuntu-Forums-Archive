---
title: "lightdm question"
date: 2012-03-07
forum: Desktop Environments
---

### Post by Diametric on 2012-03-07
Hello,

Why has /usr/lib/lightdm/lightdm been added to $PATH?  

Thanks!

---

### Post by wojox on 2012-03-07
Did you add it somewhere?

```
wojox@wojox-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
wojox@wojox-desktop:~$
```

I don't seem to have it.

---

### Post by Toz on 2012-03-08
I do. 
```
$ echo $PATH
/home/toz/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
It might be related to this: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/868363]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/868363"). From what I understand, it allows you to change users (using gdmflexiserver) from the screensaver. 

EDIT: Just checked. It actually works for me (using Xubuntu and xscreensaver). Cool.

---

### Post by Diametric on 2012-03-08
Ah - I bet that's it.  Thanks for the replies...I'm an only user on my box, so I'm going to remove it.  

Cheers!

---

### Post by wojox on 2012-03-08
> **Toz said:**
> From what I understand, it allows you to change users (using gdmflexiserver) from the screensaver. 

Cool, I'll have to check that out later. :P

---

### Post by noloader on 2013-01-21
> **Diametric said:**
> Ah - I bet that's it.  Thanks for the replies...I'm an only user on my box, so I'm going to remove it.  

Were you able to remove the software? I seem to recall trying to remove Unity in the past. It did not go well because its buried in like a virus.

Could you share how you removed it?

Jeff

---

