---
title: "shutdown launcher?"
date: 2005-09-14
forum: Desktop Environments
---

### Post by vr04 on 2005-09-14
Hi everyone,

I'm trying to add a launcher to my desktop that'll run the command
```
sudo shutdown -h now
```
I check the box to make it run in the terminal. When I launch it, it naturally asks for the password. What I'd like to do is incorporate the password in my command line - in the launcher.

I tried
```
sudo shutdown -h now | password
```
but that of course didn't work.

In the #ubuntu channel, I was told that this is impossible, which I don't think makes sense... but please, correct me if I'm wrong, or show me how this could be done.

Many thanks!

---

### Post by xaverx on 2005-09-16
You can try edit /etc/sudoers and add permission to your local user.

---

