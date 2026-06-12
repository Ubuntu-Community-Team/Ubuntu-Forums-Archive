---
title: "help"
date: 2005-02-06
forum: Desktop Environments
---

### Post by pavel on 2005-02-06
dear friends, when installing ubuntu i couldn't define myself as root.
i've heard ubuntu doesn't use root but another word like "subo", i'm not shure if i've written it right. if somebody can help me in this problem i'd be happy.
and what should i do to play mp4 files?
thanks, pavel

---

### Post by mirons on 2005-02-06
"sudo" is not a username, but a program that allows some users (in the case of ubuntu the first user you created during installation) to run programs with root (or other users) privileges. When asked you have to type your user password. (e.g. 'sudo bash' starts a root shell).

---

### Post by Razvan on 2005-02-06
if you would like to have a root account, you can use

```
sudo passwd root
```

to give a password to the root user and then login as root

---

