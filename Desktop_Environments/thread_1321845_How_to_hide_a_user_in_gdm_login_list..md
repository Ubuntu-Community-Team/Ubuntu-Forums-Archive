---
title: "How to hide a user in gdm login list."
date: 2009-11-10
forum: Desktop Environments
---

### Post by Huufarted on 2009-11-10
I couldn't find an answer, so I did some research.

Have a list of a bunch of Ubuntu users, perhaps purely for ssh utility or to allow friends to sftp in, but don't want them to show up in the gdm login list as of Karmic Koala?

the gdm login list lists any Ubuntu login user with a UID >=1000

This means as long as you get a login set to use a UID <1000 it will NOT show up in the gdm login list.

here's how:  System -> Administration -> Users and Groups

Edit the user by click on properties, go to advanced, then change the "User ID" to a different number.  Try and make sure it's not already used by another person by looking at /etc/passwd

Additionally, can someone tell me (and others) the purpose of the UID and what benefits it provides and if anything negative will happen if 2 users share the same UID?

---

### Post by Simian Man on 2009-11-10
> **Huufarted said:**
> Additionally, can someone tell me (and others) the purpose of the UID and what benefits it provides and if anything negative will happen if 2 users share the same UID?

For starters, UIDs are used for the permission system, so if two users share a UID they will have the same permissions on files and such.  Why would you *want* two users to share a UID?

Nice tip about GDM by the way.

---

### Post by Huufarted on 2009-11-10
Simian Man, the real purpose was to give users a valid reason why they would NOT want two users to have the same UID, that's all.

---

