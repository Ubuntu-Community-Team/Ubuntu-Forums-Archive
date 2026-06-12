---
title: "moving files into permission restricted directories"
date: 2009-01-31
forum: General Help
---

### Post by retnum on 2009-01-31
Hi.

I'm trying to move a couple library files (.so) from ...
~/triss/libs to /usr/bin.

I can't do it because of permissions denial.
I've tried using sudo mv -t /usr/bin but it doesn't work,I can't understand the help file for mv it's so unclear.

Can you help me before I jump under the next bus please?

---

### Post by sameep on 2009-01-31
Hi ,

Try typing sudo su in the terminal , put your password in. After that use the mv command. It should help.

---

### Post by Nepherte on 2009-01-31
Just prefix the mv command with sudo. I doubt sudo su will work since the root account is disabled.

---

### Post by Yashiro on 2009-01-31
Open a terminal at ~/triss/libs.
Enter sudo -i
Copy whatever.
Type exit.

---

### Post by scouser73 on 2009-01-31
Type **gksudo nautilus** enter your password, and you can then move the files.

---

### Post by sameep on 2009-01-31
> **Nepherte said:**
> Just prefix the mv command with sudo. I doubt sudo su will work since the root account is disabled.

sudo su does work .

sameep@sameep-desktop:~$ sudo su
[sudo] password for sameep:
root@sameep-desktop:/home/sameep# 


Regards,

Sameep

---

### Post by geirha on 2009-01-31
> **retnum said:**
> Hi.

I'm trying to move a couple library files (.so) from ...
~/triss/libs to /usr/bin.



On the matter of where to put the libs though. The libs should not go in bin/, they should go in lib/. And secondly, to keep things a little more tidy, I recommend you put the libs under /usr/local/lib/ and not /usr/lib/. Makes it easier to separate files installed by deb-packages (under /usr) and files installed manually (under /usr/local).

```
sudo cp ~/triss/libs/* /usr/local/lib/
```

Both /usr/local/lib and /usr/lib is in the path of ld.

---

