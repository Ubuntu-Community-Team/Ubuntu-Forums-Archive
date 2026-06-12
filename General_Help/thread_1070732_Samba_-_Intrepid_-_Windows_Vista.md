---
title: "Samba - Intrepid - Windows Vista"
date: 2009-02-15
forum: General Help
---

### Post by tiger.woods on 2009-02-15
I'm trying to use Samba with Vista and would like the user on my Vista machine to be able to login to a shared directory on Intrepid.

Do I need to add the user in Ubuntu, is this just like adding a regular user? Is there a how-to for this somewhere?

Thanks.

---

### Post by daniel014 on 2009-02-15
If you get the Samba program and set up a new share, you can control who opens and edits your shares with passwords.

---

### Post by Nepherte on 2009-02-15
Here's a good thread to start with: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

If you want users to authenticate before accessing a share, you will have to use the option:
```
security = user
```
in /etc/samba/smb.conf

Besides that, you will need to create the users (you want to login) on your linux samba server and set a password:
```
sudo useradd -s /bin/false <username>
sudo passwd <username>

```
 Afterwards you add the users to samba and enable the account:
```
sudo smbpasswd -a <username>
sudo smbpasswd -e <username>
```

I believe that's about it.

---

### Post by tiger.woods on 2009-02-15
So by changing security=user that will mean that each person that will be accessing a samba share will need credentials on the box correct?

> 
sudo useradd -s /bin/false <username>

Does this actually create a /home directory for the user or just add them to the box?

[EDIT]

Worked as instructed.

---

