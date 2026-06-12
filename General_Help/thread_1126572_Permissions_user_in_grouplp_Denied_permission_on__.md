---
title: "Permissions: user in group:lp Denied permission on  lp command"
date: 2009-04-15
forum: General Help
---

### Post by ncmncm on 2009-04-15
Hi all
Can  someone help me  figure out this issue. While trying to understand users and groups in detail, I  tried experimenting with lp.
I want to make lp accessible only to members of lp group
Here is what I  did:

1. /usr/bin/lp originally belonged to root. 

> -rwxr-xr-x 1 root root 17872 2009-03-26 12:09 /usr/bin/lp


2. I changed its ownership to user: lp and  group lp

> sudo chown lp /usr/bin/lp 
> sudo chgrp lp /usr/bin/lp 

 Result: 
> -rwxr-xr-x 1 lp lp 17872 2009-03-26 12:09 /usr/bin/lp

3. Next I removed x permissions for others

> sudo chmod o-x /usr/bin/lp 

 Result: 
> -rwxr-xr-- 1 lp lp 17872 2009-03-26 12:09 /usr/bin/lp


4.Set passwd for lp
> sudo gpasswd lp


5. Added user:user to group lp
My /etc/group looks like this
 Result: 
> lp:x:7:user

My /etc/gshadow looks like this
> lp:NF4MRx5U1YATM::user


6. When I now, as user, use lp, I get the following error:
**> bash: /usr/bin/lp: Permission denied**


What am I  failing to understand?

---

### Post by ncmncm on 2009-04-15
anyone?

---

### Post by _Purple_ on 2009-04-15
Is lp a file?
Which command triggered the error "bash: /usr/bin/lp: Permission denied" ?

---

### Post by ncmncm on 2009-04-15
> **_Purple_ said:**
> Is lp a file?
Which command triggered the error "bash: /usr/bin/lp: Permission denied" ?


yes, thats correct.
From Bash shell, 

> ncmncm>lp 
bash: /usr/bin/lp: Permission denied

---

### Post by ncmncm on 2009-04-16
anyone?

---

### Post by maheshasolkar on 2009-04-16
When you are 'lp', can you run the following commands and post the output?

```
  whoami
  which lp
  ls -al `which lp`

```

---

### Post by ncmncm on 2009-04-16
> **maheshasolkar said:**
> When you are 'lp', can you run the following commands and post the output?

```
  whoami
  which lp
  ls -al `which lp`

```



lp is just a user  for printing. Has no login . 
A group by the same name also exists.

---

### Post by ibuclaw on 2009-04-17
For anyone who runs into this thread.

If you add yourself to a group, you must logout/login again for that new group membership to take effect.

I trust it now works for you ncmncm, since it has been a day since you last sent a message, and from reviewing what you have given, it does appear that it should work now, presuming you have at least logged out and at most shutdown your computer during the time you haven't been here. ;)

Regards
Iain

---

### Post by ncmncm on 2009-04-17
Thanks Iain. I was lost in some otehr issues and forgot this completely. And I  just tried it. It works . The logout/login is the key. 

Cheerio
ncm

---

