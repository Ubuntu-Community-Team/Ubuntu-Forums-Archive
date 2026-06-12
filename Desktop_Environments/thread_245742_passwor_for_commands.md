---
title: "passwor for commands"
date: 2006-08-28
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-08-28
I am trying to set up java using the terminal.After typeing su it ask for password. Forgive my ignorance, but what eould be the password? I tried my system p-word but that was not. I'm stuck!!](*,)

---

### Post by Jussi Kukkonen on 2006-08-28
su logs in as superuser (root). The root account is not enabled by default.

Are the instructions you use for ubuntu? This should be all you need  to do on Ubuntu 6.06 to install Sun java:
```
sudo apt-get install sun-java5-bin

```

if you really want a root shell, *sudo -s* should do it.

---

### Post by Ramses de Norre on 2006-08-28
Check [this]("http://wiki.ubuntu.com/RootSudo").

---

