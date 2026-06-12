---
title: "Root not superuser anymore!"
date: 2005-08-30
forum: Desktop Environments
---

### Post by samba on 2005-08-30
Hi,

I've got a strange problem. As a first thing, I should say that I cannot explain how it happens, as this is on a public computer, so people may have done many things on it that I'm not aware of. But the problem is the following.

It seems that "root" is not the superuser anymore. When I login in my account, sudo works, but I cannot execute anything that the root user would normally be able to do. The /etc/sudoers file is fine, this is not the problem.

So I tried to boot in recovery mode, which should normally boot a root console. But it booted a console which instead of root logged in a "I have no name!" account, that is

```

I have no name!@high:~$

```

(high is the computer name) Then I couldn't do anything that superuser should be able to do, as it was saying (if I remember well) that uid0 had no name.

So it seems to me that root is not the superuser anymore, and that uid0 is the superuser but has no name! I don't know what happened, but this is the situation now. We can't do anything as root anymore.

Obviously, I could reinstall ubuntu, but i'd prefer an easier solution as there's quite a bit of configuration to do on that public computer.

Anyone's got any idea on how to solve this problem?

thanks :-)

vincent

---

### Post by samba on 2005-08-30
Ok, after having read a bit on superuser on the web (i'm no expert in linux at all), i found that UID=0 means that the user is a superuser. Then I looked in the /etc/passwd, and this is the problem; there is no supeuser anymore. The /etc/passwd file is
```

root:x:1:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
postfix:x:100:103::/var/spool/postfix:/bin/false
syslog:x:105:105::/home/syslog:/bin/false
klog:x:106:106::/home/klog:/bin/false
guest:x:1000:1000:guest,,,:/home/guest:/bin/bash
messagebus:x:101:110::/var/run/dbus:/bin/false
cupsys:x:102:107::/:/bin/false
fetchmail:x:103:65534::/var/run/fetchmail:/bin/sh
hal:x:111:111:Hardware abstraction layer,,,:/var/run/hal:/bin/false
saned:x:113:113::/home/saned:/bin/false
gdm:x:104:114:Gnome Display Manager:/var/lib/gdm:/bin/false
+::::::

```

So one can see that the UID of root is (for some unknown reason) 1, and there is no user with UID=0, so no superuser. However, as there is no superuser anymore i cannot modify this file (or any other file that asks for superuser permissions), and i cannot modify it from a recovery boot as usual. I could boot say knoppix (if i had a copy with me now) and modify the file that way i suppose. But is there any way i can do it directly from ubuntu?

Thanks :-)

vincent

---

### Post by Sam on 2005-08-30
Use the live CD if you have it. It's the only way to do this (except plugging your hard disc in an another linux box).

---

### Post by samba on 2005-08-30
Thanks. But anyway I found my Knoppix CD. Problem solved! :-)

---

### Post by bigtree1316 on 2006-11-21
samba,

Could you tell me how you did it with the Knoppix CD?

thx,

---

