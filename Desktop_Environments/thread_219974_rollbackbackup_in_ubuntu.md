---
title: "rollback/backup in ubuntu"
date: 2006-07-20
forum: Desktop Environments
---

### Post by dus_10 on 2006-07-20
i've made some installations and changes to ubuntu and i dont like some of them, so i was wondering if there is a way to rollback my system, or if backup files are automaticly saved on my system, kinda like windows has, because i have made so many changes that i will have to reinstall dapper completely unless someone can help ?

---

### Post by aysiu on 2006-07-20
I believe Synaptic keeps a thirty-day history of what you've installed.

Otherwise, I don't believe there are restore points. You can always create a restore point with PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

You may also want to think about creating a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by dus_10 on 2006-07-20
alright, i just tryed looking in synaptic, but as soon as i launch it, a message comes up that says i cant make changes because i am not running in root, and i have no clue why, because my user name is the only one on this computer..

---

### Post by aysiu on 2006-07-20
What happens when you paste this command into the terminal? ```
gksudo synaptic
```

---

### Post by dus_10 on 2006-07-20
that makes the message not come up, and it also asked for my password, thanks, now where do i find the 30 day thing u were talking about ?

---

### Post by aysiu on 2006-07-20
> **dus_10 said:**
> that makes the message not come up, and it also asked for my password, thanks, now where do i find the 30 day thing u were talking about ?
Well, I think the default is to keep history or for 30 days at least. Unfortunately, as I'm poking around, it seems the history is just history--there isn't an automated way to rollback installations...

---

### Post by Thund3rstruck on 2006-07-21
-

---

### Post by Thund3rstruck on 2006-07-21
You could generate a list of installed packages and then batch remove the ones you don't want..

```

$sudo dpkg --get-selections |grep '[[:space:]]install$' | awk '{print $1}' > packages

```

Delete the ones you want to keep from packages and then run

```

$sudo apt-get remove -y `cat packages`

```

---

### Post by dus_10 on 2006-07-21
alright... thanks

---

