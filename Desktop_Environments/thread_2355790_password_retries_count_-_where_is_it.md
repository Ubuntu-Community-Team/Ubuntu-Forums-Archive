---
title: "password retries count - where is it?"
date: 2017-03-16
forum: Desktop Environments
---

### Post by alabamatoy2 on 2017-03-16
Ubuntu 16.04.2, Unity desktop, Need to set password retries allowed for all users, where is this setting?

---

### Post by TheFu on 2017-03-17
pam-tally - [https://ubuntuforums.org/showthread.php?t=1024263](https://ubuntuforums.org/showthread.php?t=1024263)

But if someone has physical access to the machine and they already have knowledge to login (even if it has whole disk encryption), then they can bypass anything you put in place.

For ssh failed passwords, use something like fail2ban or denyhosts.  Of course, passwords should never be allowed after the first 5 minutes for remote user authentication. Keys should be mandatory.

---

### Post by alabamatoy2 on 2017-03-23
> **TheFu said:**
> But if someone has physical access to the machine and they already have knowledge to login (even if it has whole disk encryption), then they can bypass anything you put in place.

Yes, I understand that.  But sometimes you gotta do what the boss says, even when it makes less than perfect sense.  :-)  Thanks for the link, that was exactly what I needed.

---

