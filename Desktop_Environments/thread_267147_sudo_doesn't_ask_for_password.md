---
title: "sudo doesn't ask for password"
date: 2006-09-28
forum: Desktop Environments
---

### Post by albinoloverats on 2006-09-28
Well the title pretty much explains what's going on.  Each time I use sudo it no longer asks for my password.  This I feel is somewhat of a security risk.

If anybody knows what might have happened and/or how to resolve this any help would be appreciated.

---

### Post by RichJacot on 2006-09-28
The timeout for asking the password again is something like 10 minutes.  Is it not asking you the password again even after that?

---

### Post by orb9220 on 2006-09-28
Yes I noticed that too. It some kind of timeout thing. do a sudo in term  wait then try again.

I kinda like the idea so if I have to run a few sudo's I don't waste time or keypresses.

I think it may be connected to the term window too. Because closing the term and launching a new term I still don't get asked for password.
same for gksudo.

---

### Post by albinoloverats on 2006-09-28
I knew it would remember for a short period of time, but this is happening even off a reboot! :S

---

### Post by ayoli on 2006-09-28
try:
```
sudo -K
```

> from man:  -K  The -K (sure kill) option is like -k except that it removes the user’s timestamp entirely.  Like -k, this option does not require a password.

---

### Post by mac57 on 2006-09-28
Just a thought. You haven't messed with file /etc/sudoers, have you? This controls sudo's behavior. I have purposely messed with mine so that I don't have to put up with the password prompting all the time. Less secure but more convenient. So, if you have been able to make changes to /etc/sudoers (and ubuntu seems to go to GREAT lengths to stop you from doing this) this may be responsible.

---

### Post by albinoloverats on 2006-09-28
> **mac57 said:**
> Just a thought. You haven't messed with file /etc/sudoers, have you? This controls sudo's behavior. I have purposely messed with mine so that I don't have to put up with the password prompting all the time. Less secure but more convenient. So, if you have been able to make changes to /etc/sudoers (and ubuntu seems to go to GREAT lengths to stop you from doing this) this may be responsible.

I think I've figured it out - I'm a member of the admin group, and the admin group is allowed to use sudo no questions asked as noted in /etc/sudoers

---

### Post by ingo on 2006-09-28
> **mac57 said:**
> Just a thought. You haven't messed with file /etc/sudoers, have you? This controls sudo's behavior. I have purposely messed with mine so that I don't have to put up with the password prompting all the time. Less secure but more convenient. So, if you have been able to make changes to /etc/sudoers (and ubuntu seems to go to GREAT lengths to stop you from doing this) this may be responsible.

easier way is to do 

$ sudo bash

enter your password and Bob is your uncle :-D

---

