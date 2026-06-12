---
title: "I dont know root password?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by vzdesic on 2006-04-12
Hi,

during instalation of Ubuntu 5.10 I was not asked to write root password. I was asked only for additional user's password. After instalation I tried to log as root with 'su' command but because I dont know password I cant do it.

Am I misunderstand something? How to know root password?

Vedran

---

### Post by Darkriser on 2006-04-12
security feature. yup, there's none root pasword. you simply don't need it. read here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by OffHand on 2006-04-12
```
sudo passwd root
```
It will ask to enter your password (this will be your account password).
After that you will have to type your root password twice and you are done.
Usually you can just use the 'sudo' command though.

---

