---
title: "no sudo?"
date: 2006-02-26
forum: Desktop Environments
---

### Post by ubuntum0nk3y on 2006-02-26
Ok, so I installed Ubuntu for a friend and got it working nicely. 

I had been using an account under my name (user_a) to do the work, and when the system was ready to be handed off, I created an account for him (user_b) with admin priveleges, and deleted my account. (user_a)

The problem now is that when I try to perform sudo commands as him (user_b), nothing happens. I get prompted for the password then get returned to the command line as though it ran successfully, but the command does not work. (any command. cp, rm, vi, etc)

The same thing happens if I try to launch an app such as the Users and Groups app. I get prompted for the password, then it goes away and I never get the chance to add a user.

So, is it possible to fix this? Or have I completely borked everything?

---

### Post by Chemicalvamp on 2006-02-26
go into the system settings/user accounts or something.. and make sure "sudo" is in his secondary groups

---

### Post by RAOF on 2006-02-26
[QUOTE=Chemicalvamp]go into the system settings/user accounts or something.. and make sure "sudo" is in his secondary groups[/QUOTE]
...except he won't be able to access the users/groups config thing because he doesn't have sudo rights! :-k 

To check that user_b should have sudo access, run "groups" from a terminal - that should show what groups he's a member of.  He should be a member of "admin".

You'll need to boot into "recovery mode" to fix any of this though.  If user_b is not a member of admin, you'll need to "adduser *user_b* admin".  If he is a member of admin, check out the /etc/sudoers file - it should look like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

---

