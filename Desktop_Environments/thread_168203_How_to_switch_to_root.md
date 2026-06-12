---
title: "How to switch to root"
date: 2006-04-30
forum: Desktop Environments
---

### Post by ddavid123 on 2006-04-30
I need to log in as root so I can use apt-get.  I was never given the option to enter a root password when I installed ubuntu.  How can I set the root password when I am logged in as user only?  I need to use apt-get in the command line because I cannot update the repositories for Wine.  I try to add a apt line in synaptic, but the files needed to update the repositories fail to load with a fail or hit error.  Please help me!

---

### Post by sYs^ on 2006-04-30
try this: sudo apt-get update

It'll ask for a password, just type your user's pass. There aren't a special root password by default in ubuntu.

---

### Post by towsonu2003 on 2006-04-30
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

offtopic: I think ubuntu wikis don't show up in google easily bc of the http**s**

---

