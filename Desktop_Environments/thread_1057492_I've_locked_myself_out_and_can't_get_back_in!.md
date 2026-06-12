---
title: "I've locked myself out and can't get back in!"
date: 2009-02-01
forum: Desktop Environments
---

### Post by drewtam on 2009-02-01
No matter what user I use, administration of users has been locked and I can't get back in control. I've got all my passwords, but nothing seems to make a difference.

Examples:

User 1
system>administration>User and Groups

>unlock

"Could not authenticate
An unexpected error has occurred."

User 2
system>administration>User and Groups

>unlock

sudo doesn't allow me to view or something or other. Doesn't even give me the option to enter root password.

What's up? I don't know what I did to screw this up.

System info:
Dell Dimension 8300
Ubuntu 8.10 Intrepid Ibex

Installed Ubuntu about 4days ago.

---

### Post by p_quarles on 2009-02-01
Are you able to boot into "Recovery" mode from the Grub boot menu at startup? If so, I can give you some commands that will create a fresh user with which you can try to diagnose the issue.

EDIT: Also, if you are unable to boot into Recovery mode, please let us know what error you get.

---

### Post by drewtam on 2009-02-02
Yes, I can use grub to boot into recovery mode. After selecting that option, it gives me several more options. I think one was repair x-something, another was command terminal, continue to boot normal, and one more I can't remember.

---

### Post by p_quarles on 2009-02-02
> **drewtam said:**
> Yes, I can use grub to boot into recovery mode. After selecting that option, it gives me several more options. I think one was repair x-something, another was command terminal, continue to boot normal, and one more I can't remember.
Okay, so boot into the command line and enter the following commands:
```
useradd -m test
```
This will create a new user named "test".  Now, set a password:
```
passwd test
```
This will prompt you for a password for this new user. You'll need to enter it twice.
Then:
```
adduser test admin
```
This will add the user to the "admin" group, which by default has sudo privileges on the Ubuntu system. Once you've done all this:
```
reboot
```
which will restart the system. From there, boot up as normal, and log in as the user "test." Attempt to do something that requires sudo privileges, like start up Synaptic.

If you are able to log in with this user and run a normal session, then the initial problem was with the other account. If you aren't able to run a normal session with the test user, something is more likely wrong with the system itself.

---

### Post by drewtam on 2009-02-04
> **p_quarles said:**
> Okay, so boot into the command line and enter the following commands:
```
useradd -m test
```
This will create a new user named "test".  Now, set a password:
```
passwd test
```
This will prompt you for a password for this new user. You'll need to enter it twice.
Then:
```
adduser test admin
```
This will add the user to the "admin" group, which by default has sudo privileges on the Ubuntu system. Once you've done all this:
```
reboot
```
which will restart the system. From there, boot up as normal, and log in as the user "test." Attempt to do something that requires sudo privileges, like start up Synaptic.

If you are able to log in with this user and run a normal session, then the initial problem was with the other account. If you aren't able to run a normal session with the test user, something is more likely wrong with the system itself.

Problem solved first try!
Deleted the broken users and created new ones.

Thanks:KS

---

