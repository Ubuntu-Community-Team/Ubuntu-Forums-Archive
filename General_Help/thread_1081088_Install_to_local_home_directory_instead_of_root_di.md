---
title: "Install to local home directory instead of root directory ?"
date: 2009-02-26
forum: General Help
---

### Post by ramvi on 2009-02-26
My university is running an old version of Red Hat. How to I go about compiling and using aptitude / dpkg in my local directory (and apt-get must be told to install to my local Home directory). That is, install to ~/usr ~/bin etc istead for /usr /bin

How do I go about doing this? I can't be the first person who try to achieve this

---

### Post by Xiong Chiamiov on 2009-02-28
Most packages are going to need to place links in system directories, and installing new packages next to old ones is just asking for trouble.  I suppose you could chroot into your home directory.

---

### Post by ramvi on 2009-03-02
Thanks for understanding and answering my question!

> **Xiong Chiamiov said:**
> Most packages are going to need to place links in system directories
Hmm, but many applications, like Firefox, should be able to run as long as you have the executables. What I hope to do is run applications like nautilus etc. locally.


> **Xiong Chiamiov said:**
>  and installing new packages next to old ones is just asking for trouble
Bring it on!


> **Xiong Chiamiov said:**
> I suppose you could chroot into your home directory.
Great idea! Though I don't have sudo privileges..
jondr@login2 ~ $ chroot chroot/
chroot: cannot change root directory to chroot/: Operation not permitted
Is there an other solution?

---

### Post by Slim Odds on 2009-03-02
> **ramvi said:**
> My university is running an old version of Red Hat. How to I go about compiling and using aptitude / dpkg in my local directory (and apt-get must be told to install to my local Home directory). That is, install to ~/usr ~/bin etc istead for /usr /bin

How do I go about doing this? I can't be the first person who try to achieve this

First, it's "/usr/bin" not "/usr /bin"

You can put executable stuff under your home directory and then prepend that directory to your path.

for example: put a new lib that you want to override the system lib into ~/bin

then```
export PATH=~/bin:$PATH
```I'm not sure how path handles ~
You might have to spell out the actual name

**NOTE: You might break stuff.**

---

