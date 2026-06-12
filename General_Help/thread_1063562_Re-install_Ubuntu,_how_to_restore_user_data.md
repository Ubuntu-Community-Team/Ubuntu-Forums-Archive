---
title: "Re-install Ubuntu, how to restore user data?"
date: 2009-02-08
forum: General Help
---

### Post by UranUtan on 2009-02-08
Hi,

I have a fine working Ubuntu 8.10 x32 Desktop on a decent computer. I had installed some Windows games to run under Wine 1.1.14. There might be some graphics modes incompatibilities or something bad I don't really understand. In short, something had screwed up the graphics settings. It's a little bit long to describe here, as I have already written several threads and had no good answer.

So I decide to re-install Ubuntu on top of the existing one. I would like to preserve the user data and configuration. There are 3 user accounts on the system. What should I do?

The partition layout is:
Partition /dev/sda1 ext3:  10G for root
Partition /dev/sda5 ext3: 145G for /home
Partition /dev/sda6 swap

Thank you very much in advance for any help.

---

### Post by taurus on 2009-02-08
Do a normal install until you get to the partition screen.  Pick Manual option and mount /dev/sda1 to / and format it.  Then, mount /dev/sda5 to /home but DO NOT format that partition.  You don't have to do anything with /dev/sda6 since the installer knows how to handle the swap partition.  In fact, the installer even uses the swap partition.

Make sure you create your username the same as the one from /home so you can have all your settings when you first log back in.  Then, create the other two accounts exactly like they were, in the right order too since the next user should have an UID of 1001 and the other should have an UID of 1002 (while the first account is 1000).

---

### Post by UranUtan on 2009-02-08
> **taurus said:**
> Then, create the other two accounts exactly like they were, in the right order too since the next user should have an UID of 1001 and the other should have an UID of 1002 (while the first account is 1000).

Just to make 100% sure, is there anyway to query on my current Ubuntu setting what is the username of UID 1001 and 1002?

How exactly should I recreate a user? Same user name, OK. But should it have same password, same full name, etc.

Sorry for the silly questions but this is going to be my first complex exercise with Ubuntu installation. Just want to ensure to make it right.

---

### Post by jocko on 2009-02-08
> **UranUtan said:**
> Just to make 100% sure, is there anyway to query on my current Ubuntu setting what is the username of UID 1001 and 1002?

How exactly should I recreate a user? Same user name, OK. But should it have same password, same full name, etc.

Sorry for the silly questions but this is going to be my first complex exercise with Ubuntu installation. Just want to ensure to make it right.
The users uid's are probably listed in /etc/passwd:
```
cat /etc/passwd
```Or:
```
grep 1001 /etc/passwd
grep 1002 /etc/passwd
```Don't know if you need to have the same password or full name. Probably not, since the password is not stored in the users home folder.

---

### Post by UranUtan on 2009-02-08
Hi jocko,

Saw the UID + user name listed in /etc/passwd as you instructed.
Thanks very much.

---

