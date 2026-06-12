---
title: "Elevated rights from AD groups"
date: 2016-03-31
forum: Desktop Environments
---

### Post by guilly on 2016-03-31
Hi,

I'm trying to grant my users rights to install software and run commands under sudo. What I've done is the following:

- Created an LDAP group
- modified visudo to permit the new group sudo access to all commands (%group ALL=(ALL) ALL)

This seems to work, but what I can't seem to get to work is if the user launches software center. I'd like for the user to be able to get prompted for their password and then be granted rights to install the software. How can I achieve this ?

Thanks,

---

