---
title: "stripped user to create users"
date: 2007-08-20
forum: Desktop Environments
---

### Post by cetheriel on 2007-08-20
i've installed ubuntu on a pc from the medialab i work on.
since we are almost a 100 people working here, i don't want to create several users.
instead, i wanted to create a user that could only create new users. it should not edit other users privileges, nor connect to the internet, nor anything else. i managed to create a user that has only administrative rights, but does not connect to internet, nor reads CDs nor whatever.
points are: 
* it can still run most of applications: if he does, no one will create their own users, but rather use this one. believe me, they're lazy.
* it can run other system admin tools. i don't want this user to do that.
* it can edit other users privileges. this is something i definitely don't want this user to be able to. the password will be written near the pc, so that everyone can create their own user. but it also means i have to make sure this user does nothing else.

---

### Post by raijinsetsu on 2007-08-20
I think the functionality you're looking for would best be done with sudo. Make a normal user(in no groups) and edit the sudoers file so they can run "useradd..." or whichever alternative you're looking for... That's what we did for our *nix lab.

---

### Post by eentonig on 2007-08-20
Wouldn't it be easier to just 'batch-create' all those user accounts.

---

### Post by raijinsetsu on 2007-08-20
> **eentonig said:**
> Wouldn't it be easier to just 'batch-create' all those user accounts.

Only if you know what users you'll have.

---

### Post by cetheriel on 2007-08-20
> **raijinsetsu said:**
> I think the functionality you're looking for would best be done with sudo. Make a normal user(in no groups) and edit the sudoers file so they can run "useradd..." or whichever alternative you're looking for... That's what we did for our *nix lab.

wonderful. how do i do that?

---

