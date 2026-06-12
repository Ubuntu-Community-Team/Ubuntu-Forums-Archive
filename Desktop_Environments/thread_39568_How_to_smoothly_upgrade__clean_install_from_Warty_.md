---
title: "How to smoothly upgrade / clean install from Warty to Hoary?"
date: 2005-06-05
forum: Desktop Environments
---

### Post by erik-the-red on 2005-06-05
I have partitioned my system as follows:

1. /
2. /usr
3. /tmp
4. /home

What should I do to smoothly upgrade or even clean install from Warty to Hoary?

---

### Post by shof2k on 2005-06-06
To upgrade, change your /etc/apt/sources.list from Warty to Hoary, then type
**sudo apt-get update**
**sudo apt-get dist-upgrade**

OR
You can download the hoary iso and perform a clean install.

---

### Post by erik-the-red on 2005-06-06
[QUOTE=shof2k]To upgrade, change your /etc/apt/sources.list from Warty to Hoary, then type
**sudo apt-get update**
**sudo apt-get dist-upgrade**

OR
You can download the hoary iso and perform a clean install.[/QUOTE]
 Well, it worked.

Now, I'm using Ubuntu Hoary.

---

### Post by shof2k on 2005-06-07
nice one.  Welcome to ubuntu :)

---

