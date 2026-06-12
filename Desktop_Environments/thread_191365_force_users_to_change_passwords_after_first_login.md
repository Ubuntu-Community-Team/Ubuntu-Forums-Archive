---
title: "force users to change passwords after first login"
date: 2006-06-07
forum: Desktop Environments
---

### Post by demck85 on 2006-06-07
How do I get users to change their password after the login into my server for the first time?

Scenario: System Admin. setup Bill with an account on the server with SSH access, but want Bill to change the random password the system assigned, to something that Bill will rememebr once he login in the first time with the random password.

Is there like a script that I can have run when users login the first time, that doesn't run again?

Or a file that can be moddified to do something like this??

Thanks

---

### Post by kaamos on 2006-06-07
This could help:
[quote=man passwd]-e, --expire
    Immediately expire an accounts password. This in effect can force a user to change his/her password at the users next login.
[/quote]

---

### Post by demck85 on 2006-06-07
Where would I use what you suggested? Would I have a script that would run when user login the first time? Or what?

---

### Post by katiad on 2006-06-08
I'm running Kubuntu, and I used kcontrol's users & groups tool, and indeed, it did force all my users to change their passwords when they logged in without my having to do anything special at all.

---

### Post by demck85 on 2006-06-09
But, that is with Kubuntu, what about in Ubuntu wuth GNOME?

---

