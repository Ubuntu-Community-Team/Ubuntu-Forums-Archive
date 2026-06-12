---
title: "Help text in terminal"
date: 2009-05-09
forum: General Help
---

### Post by haveblue on 2009-05-09
I just installed Jaunty from the Dell custom DVD, and everything is working great. 

My only issue is when I launch a terminal, I get some text at the top, which I haven't gotten on previous installs.

> 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


How can I change (read: remove) this?

Thanks :)

---

### Post by Claus7 on 2009-05-09
Hello,

this message usually appears if you run the live CD without really installing the operating system in your hdd. Are you sure you did the installation and not just running the cd? Do you still have the cd in your tray?

Regards!

---

### Post by Titan8990 on 2009-05-09
I believe that is stored in /etc/motd.

---

### Post by haveblue on 2009-05-09
> **Titan8990 said:**
> I believe that is stored in /etc/motd.

Unfortunately, /etc/motd doesn't contain the same text, so that's not where it's coming from. :(

---

### Post by haveblue on 2009-05-09
Hmm.. well, it seems to have disappeared while I was searching for it. Maybe I just had to run something as sudo to make it go away?

Thanks guys

---

### Post by Claus7 on 2009-05-09
Hello,

does this link help? It is supposed to be a bug.
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

edit: If I understood correctly you just typed a sudo command and it disappeared. 

Regards!

---

### Post by todak on 2009-05-09
You must use the sudo command before it will disappear.

---

