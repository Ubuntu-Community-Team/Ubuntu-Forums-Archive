---
title: "Basic chroot jail questions"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Anonii on 2006-09-16
Greetings,

I set up a chroot jail today. I knew only basic stuff about chroot and the [guide]("https://wiki.ubuntu.com/DebootstrapChroot") didnt give much information on what it was, just on how to create it. 

So, I can now login to the chroot enviroment by using "dchroot -c mychroot -d
" I want to use it, mainly to build software packages. So I moved a file throu the console, but it was moved in the normal enviroment too. So what kind of "jail" does that chroot sandbox gives?

Thanks!

---

### Post by statue on 2006-09-16
If I understand your question correctly...it protects the core of your system by not letting a piece of software have access to your 'real' root filesystem. Chrooting makes it so whatever you set up inside the chroot environment will think that basically a subdirectory of your filesystem is actually the root of the system instead. This protects the core of your computer by not letting any malicious user/code have access to everything on your box because the exploited software thinks that it's chrooted jail is all their is on your computer. Often times web servers like apache are chrooted inside a virtual jail to ensure that just in case an attacker gains access, they can only go so far inside the computer.  It's like having a backup defense. Was that at all an answer to your question?

---

