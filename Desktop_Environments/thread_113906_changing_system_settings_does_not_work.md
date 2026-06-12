---
title: "changing system settings does not work"
date: 2006-01-07
forum: Desktop Environments
---

### Post by klein-matthi on 2006-01-07
Hi,

I have a problem with my new (and first) Ubuntu installation:

For changing any system settings (like adding applics) I have to enter the root password in the gnome menu. After that nothing happens. 

Any other changes I try later on   don't require again the password, but do not open at all too.

What to do?

Opening this tools with a shell (e.g. synaptic) DOES work!

Best, 

Matthi

---

### Post by zappa86 on 2006-01-07
When you go to something that requires root access in gnome (such as synaptic) it will prompt you for your password. This is PAM, it is the autorization that is needed. It will remember you for awhile so it wont require password for a while. I know PAM sometimes craps out on me (I dont know why yet, and I would like to know) but I just restart and it usually works.

---

### Post by klein-matthi on 2006-01-08
Well, my PAM does not work everytime I boot my computer. And how to restart it, when the system is running?

I tried ti find it in /etc/init.d but failed.

---

