---
title: "Installing LAME through repo?"
date: 2005-09-10
forum: Desktop Environments
---

### Post by erik-the-red on 2005-09-10
Is there anyway I can install LAME via aptitude?

---

### Post by Daniel G. Taylor on 2005-09-10
LAME is available from the Multiverse repositories. If you haven't already done so, you probably want to add the Universe and Multiverse repositories to your apt sources list.

In Synaptic you can go to Settings -> Repositories and add "universe multiverse" to the sections parts of the listed repositories (where you should already have "main restricted" listed).

Editing /etc/apt/sources.list you would put something along the lines of
```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse
```

To see which packages are available in the repositories, check out [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by erik-the-red on 2005-09-11
Thank you so much.

I was unaware of the multiverse repositories :D

---

