---
title: "cannot login as root"
date: 2009-01-02
forum: General Help
---

### Post by unix1adm on 2009-01-02
I have tried several things and cannot get the root to login directly in. I tried this page 

[http://doc.ubuntu.com/ubuntu/serverguide/C/user-management.html](http://doc.ubuntu.com/ubuntu/serverguide/C/user-management.html)

Still wont work. Now when I login as my ID and su - root I get
your account had expired; please contact your system admin
su: authentication failed.

I know the password is correct. 

please help as I cannot do anything on my laptop as my id. I need root.

---

### Post by snowpine on 2009-01-02
Check this thread out:

[http://ubuntuforums.org/showthread.php?t=1028307](http://ubuntuforums.org/showthread.php?t=1028307)

---

### Post by unix1adm on 2009-01-02
that does not tell me how to get root. I understand about sudo but I want real root.

I cannot add any users or do anything on my system. I dont know why the adm account is not working

---

### Post by snowpine on 2009-01-02
See post #4 in the thread I linked to.

---

### Post by engocoka on 2009-01-02
Can you try this:

```
sudo su
```

Should give you root access to set the current user to root.  (It worked for me)

---

### Post by unix1adm on 2009-01-02
yes I read that


In Ubuntu the root account is disabled by default. If you need to do anything as root you have to use sudo. To do what you are talking about just do:

Code:

gksu nautilus

and drag/drop away! If this is unacceptable for you just change the root password via the terminal. I won't go in to detail on how to do it here...just Google it. That's how I found out how to do it.


This did not work for me. I keep getting account is expired for the root account.

root should never expire

I am new to linux but in UNIX AIX SUN that I support etc it never expires and the admin always has access to it.

---

### Post by snowpine on 2009-01-02
You need to use Google to find the answer because we cannot talk about it here. :)

Often times, you just *think* you need root, but can actually accomplish the task with sudo. It is worth learning the default security model before circumventing it.

---

### Post by unix1adm on 2009-01-02
I think I know what i did I think i did passwd -l root which intun expired the account.

I found this link but it does nto telly ou how to unexpire it. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by unix1adm on 2009-01-02
OK I understand and respect that. I can use the default model if i can unexpire the account. I think thats my problem.

Can you PM me how to do that?

---

### Post by unix1adm on 2009-01-02
ah never mind I figured out the unlock issue. i thought it was a sudo issuebut it was a passwd cmd issue.

---

