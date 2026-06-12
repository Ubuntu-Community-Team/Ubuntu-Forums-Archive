---
title: "Root Password"
date: 2006-04-22
forum: Desktop Environments
---

### Post by JohnN on 2006-04-22
Hello Folks, Hope you are having a great Saturday evening.

I just installed Ubuntu - and though the prompts - I was never prompted to create a root password, It did prompt me to create a secondary account which I did, and I do login and use.    Is there a way to find out what the root password is?

---

### Post by Blairboy on 2006-04-22
try running a sudo command in terminal and use whatever password you currently use for your regular login.  Like "sudo gedit blah" and see what happens.

---

### Post by aysiu on 2006-04-22
There's no root password.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Dr Gonzo on 2006-04-22
```
sudo passwd root
```:)

---

### Post by aysiu on 2006-04-22
[QUOTE=Dr Gonzo]```
sudo passwd root
```:)[/QUOTE] This would be an appropriate response if JohnN has said something like: > I've already tried this whole *sudo* thing, and I'm afraid I just like a good old, traditional root/user setup that most other Linux distributions have. How can I set a root password?

---

### Post by stansaraczewski on 2006-04-22
Ubuntu does not use a ROOT account - you aren't supposed to log on as root.

I'm a newbie of sorts - but am having a great time. Ubuntu is so much easier than RHL.

---

### Post by mister lahey on 2006-04-22
I just installed it yesterday, I logged into the root account (with my user pw, I think), and just created a new password in the root account.

---

### Post by pr0-t31n on 2006-05-16
[QUOTE=JohnN]Hello Folks, Hope you are having a great Saturday evening.

I just installed Ubuntu - and though the prompts - I was never prompted to create a root password, It did prompt me to create a secondary account which I did, and I do login and use.    Is there a way to find out what the root password is?[/QUOTE]
Same exact problem; no help yet...bump.

---

### Post by aysiu on 2006-05-16
[QUOTE=pr0-t31n]Same exact problem; no help yet...bump.[/QUOTE] No help yet? See post #3 of this thread.

---

