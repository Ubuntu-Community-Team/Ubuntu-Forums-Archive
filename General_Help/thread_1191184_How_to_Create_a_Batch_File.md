---
title: "How to Create a Batch File"
date: 2009-06-18
forum: General Help
---

### Post by Seth92 on 2009-06-18
I am fairly new to Ubuntu and I would like to create a batch file containing:

cd /opt
lampp/lampp start

This needs to run as the super-user (su).

---

### Post by donkyhotay on 2009-06-18
Welcome to linux, here they're called shell scripts. If you know the commands a shell script is very easy to create, just simply copy paste that command into a text file and give it executable permissions
```

chmod u+x ./name_of_script

```
then of course you can run it anytime you want
```

sudo ./name_of_script

```
In order to run anything with root access you will have to put sudo in front the command (even if it's your own script, though not for a script that doesn't need root access). Bypassing that is a *serious* hole in your security, serious enough that it is against forum rules to explain how to do it, and a policy I completely support!

---

### Post by Seth92 on 2009-06-18
I was actually trying to avoid the terminal all together so I can start LAMPP easily from the Desktop.

---

