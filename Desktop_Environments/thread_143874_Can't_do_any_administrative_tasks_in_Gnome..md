---
title: "Can't do any administrative tasks in Gnome."
date: 2006-03-13
forum: Desktop Environments
---

### Post by beyowulf on 2006-03-13
I mean when I try to do any administrative tasks in Gnome, and get prompted for a password, it doesn't work.  If I put in the root password, I get an error message that the password was incorrect.  If I put in my regular password which I use to log in, nothing at all happens.

I can still su - root at a command prompt and have my root password work, but its a little inconvenient.

---

### Post by bjweeks on 2006-03-13
[QUOTE=beyowulf]I mean when I try to do any administrative tasks in Gnome, and get prompted for a password, it doesn't work.  If I put in the root password, I get an error message that the password was incorrect.  If I put in my regular password which I use to log in, nothing at all happens.

I can still su - root at a command prompt and have my root password work, but its a little inconvenient.[/QUOTE]

You have to login wiht a account that has admon and enter the password for that account.

---

### Post by beyowulf on 2006-03-13
How do I do that?

It appears I don't have such an account already, so I'll have to create one.

So..

su - root
adduser <usertohaveadminpriveledges> <what options>

What options and arguments do I need to supply?

Thanks!

---

### Post by chettyk on 2006-03-13
[QUOTE=beyowulf]How do I do that?

It appears I don't have such an account already, so I'll have to create one.

So..

su - root
adduser <usertohaveadminpriveledges> <what options>

What options and arguments do I need to supply?

Thanks![/QUOTE]

I haven't use this command myself, but I think the following ought to work: 

```
useradd -G admin [username]
```

Take a look at the man pages for useradd.

---

### Post by beyowulf on 2006-03-31
Sorry, haven't much time to do anything with this topic.  Anyway, I looked in /etc/group, and it seems that my regular username is next to the adm group.  So I assume I am in the admin group already.  But the above problem still exists.

---

