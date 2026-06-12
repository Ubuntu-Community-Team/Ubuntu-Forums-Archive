---
title: "User Permissions Updating?"
date: 2007-12-28
forum: Debian
---

### Post by aimran on 2007-12-28
Hi I have encountered [this problem]("http://ubuntuforums.org/showthread.php?t=256756") with my debian setup. Since I don't use other distros, was wondering if this is a debian (and it's derivatives) only problem? 

I'd like the kernel to update user groups as and when they change. Maybe when I get around to it I'll fix it (if that is a problem in the first place).

---

### Post by kidders on 2007-12-30
Hi there,

Afaik, the thread you mentioned describes a *feature* of Linux (ie not a problem). Syncing user environments with group membership changes the moment they are made would be a gross violation of account management standards, and could even be dangerous. Unfortunately, if you modify /etc/group, all Linux, Unix-like & similar systems are _supposed_ to ignore changes, by design.

The reason for this is the wide-ranging and somewhat unpredictable effect that changes to group configurations can have. To take a simple example, suppose a process running as a particular user suddenly loses access to a database it has already opened, through some sort of configuration change. I say "database", because it's a good example of a type of file that is very sensitive to security & access control issues, on a number of fronts. In that situation, as it turns out, there is no right answer to the question "What should Linux do next?".

To avoid paradoxical system states and contradictory environment information, all processes that were running before a change must be able to continue running after it, as though nothing had happened, to protect systems from crashing, filesystem corruption, security vulnerabilities, and so on.

Anyhow, I would very strongly recommend against trying to hack around this limitation.

---

