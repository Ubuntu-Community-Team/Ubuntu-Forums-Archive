---
title: "migrated users not listed in &quot;Users and Groups&quot;"
date: 2009-01-15
forum: General Help
---

### Post by raghu1111 on 2009-01-15
Hi, 
I recently installed 8.10. I was using Fedora 5 till now.

I have one user created by ubuntu called 'ubuntu'
I migrated other user entries from Fedora (/etc/passwd, shadow etc updated). Say user name is 'fedora'.

I can ssh and login as 'fedora' and it looks fine.

I logged in as ubuntu and tried to update properties for 'fedora' but it does not appear under 'System --> Administration --> Users and Groups'. How do I make 'fedora' account to be same as 'ubuntu' account?

Thanks,
Raghu.

---

### Post by raghu1111 on 2009-01-16
No one has seen such an issue? Where does "users-admin" get its users from? Does not seem to be frome /etc/passwd or similarly well known files.

---

### Post by mssever on 2009-01-16
Are the uids <= 1000?

EDIT: I meant uids >= 1000

---

### Post by raghu1111 on 2009-01-16
yes, user ids are in 500s. I changed /etc/adduser.conf to change the limits to 500 (FIRST_USER_ID etc), but still seeing this problem.

---

### Post by mssever on 2009-01-17
> **raghu1111 said:**
> yes, user ids are in 500s. I changed /etc/adduser.conf to change the limits to 500 (FIRST_USER_ID etc), but still seeing this problem.
Argh. Typo on my part. Try increasing a uid to > 1000 and see if that changes things. In Ubuntu, all user accounts have uids >= 1000. This is in contrast to some other distros.

---

### Post by raghu1111 on 2009-01-17
I could try that, but I also need to change uid of all the files owned by those users. Is there a way to make users-admin to show those users? I already changed addusers.conf (but not yet rebooted). I hope 1000 is not hard coded in the source code. That seems to too rigid.

---

### Post by mssever on 2009-01-17
> **raghu1111 said:**
> I could try that, but I also need to change uid of all the files owned by those users. Is there a way to make users-admin to show those users? I already changed addusers.conf (but not yet rebooted). I hope 1000 is not hard coded in the source code. That seems to too rigid.
Good point about the uids of all the files. I did a search in gconf-editor and came up with the following key: /apps/gnome-system-tools/users/showall . If enabled, users-admin will show all users, including users that never login. It's the only setting I've found, so I assume that 1000 might be a compile-time setting. When I used Red Hat a long time ago, user accounts began with a uid of 500, as opposed to Ubuntu's 1000, so I'm assuming that users-admin can be modified accordingly--at least if you re-compile.

---

### Post by raghu1111 on 2009-01-18
> **mssever said:**
> Good point about the uids of all the files. I did a search in gconf-editor and came up with the following key: /apps/gnome-system-tools/users/showall . If enabled, users-admin will show all users, including users that never login. 

Thanks for gconf-editor tip. "showall" is good enough and does what I need. I just need to be careful not to touch other system accounts.

Raghu.

---

