---
title: "About running background jobs with sudo"
date: 2009-02-27
forum: General Help
---

### Post by ooobooontooo on 2009-02-27
Hi,

How do I kill a job that's been run in the back with sudo? I recently did:
```
sudo emacs /etc/environment&
```
and I couldn't kill it...I tried both from my user account and from sudo....I looked it up in process table and did kill -9 as well...Also, I noticed when I did run the job in the background it didn't ask me for any password....possible security issue...I think it has something to do with the fact that I set TIMEOUT in sudoers to 0...Any comments would be appreciated. Thanks in advance.

---

### Post by justleen on 2009-02-27
you should be able to kill it with a kill -9
make sure you have the right PID ```
 ps -ef|grep emacs
```

As far as the not being asked for a passwd: you have set the timer to 0. So you only have to type your passwd once(after the timer has reset, with sudo -k or a reboot for example), after that it will remember the passwd and never expire.

---

### Post by ooobooontooo on 2009-02-28
> you should be able to kill it with a kill -9
make sure you have the right PID
I did....
EDIT: Actually, it's possible I didn't do try this with sudo that may have been why it didn't work...

> As far as the not being asked for a passwd: you have set the timer to 0. So you only have to type your passwd once(after the timer has reset, with sudo -k or a reboot for example), after that it will remember the passwd and never expire.
I was under the impression that if you set it to zero, you'd be prompted for a password every time you used the sudo command...at least that's how it's worked so far...

---

