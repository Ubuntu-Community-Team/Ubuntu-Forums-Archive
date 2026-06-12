---
title: "after-installation problems"
date: 2006-04-02
forum: Desktop Environments
---

### Post by bladez on 2006-04-02
OK. So I'm a first-time Ubuntu user. I've got this problem. I installed Ubuntu, but he installed packages to 44% (till hermes) and then showed a error about broken package, and exited installation launching Ubuntu. And now there aren' t many things, like most important Terminal etc..

When I try to fix broken packages throu Synaptic, he shows this:

```
The following problems were found on your system:
E: /var/cache/apt/archives/gnome-icon-theme_2.12.1-0ubuntu1_all.deb: corrupted filesystem tarfile - corrupted package archive

```


And another question. How do I get in with root user, if it sill exists ofcourse. It shows incorrect password (i tryed a few things).

---

### Post by Qrk on 2006-04-02
There is no Root account... you use sudo with your normal user's password.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

What I would do is make sure you have your Cd out of the drive. Then push <Ctrl<>Alt><F1> to get to a command line.

Log in again, (username, normal password) and try 

```
sudo apt-get install ubuntu-base
sudo apt-get install ubuntu-desktop
sudo apt-get -f install
```

When that jazz is done, press <Ctrl<>Alt><F7> then press <Ctrl<>Alt><backspace>

---

