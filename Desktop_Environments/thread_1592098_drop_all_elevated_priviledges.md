---
title: "drop all elevated priviledges??"
date: 2010-10-10
forum: Desktop Environments
---

### Post by pragya on 2010-10-10
Hi, i am new to ubuntu.
Whenever i mount any disk to ubuntu,and after typing the password, a new icon is created on the taskbar which says "click here to drop all elevated priviledges".

Can anyone tell me the meaning of this icon?

The icon is of harm even i click it or not but i was just curious to know more about it.

---

### Post by bprins on 2010-10-10
if you entered your root password, you are allowed to use system programs (like installing new applications via update manager), without re-entering root password all the time.

if you drop all elevated rights, you do have to re-enter the root password when you start a command that requires root privileges.

so, concluding, quite harmless. I never use it, don't really know who would. If you don't want people playing around on your PC just lock it :)

---

### Post by vek on 2010-10-11
To be more specific, when you issue a command that asks your for your password, and you type it in, it gives you super user privileges for a limited time, and during that time programs can ask for full access to every part of your machine and modify whatever.  It would be dangerous to surf the web, for example, while having elevated privileges. (I think.  I might be wrong about this, it could be that only specific applications get given access rights, instead of anything you run).

The system automatically drops you back down to a non-super-user after a specific amount of time has passed (I think), which is why you have to type the password again if you want to do another administrative action after waiting a while.

The icon that lets you drop those privileges IMMEDIATELY instead of waiting for the time to elapse.  Its good security practice to drop privileges once you're done with whatever installing or configuring or editing of config files you intended to do, so that if anything tries to access your system files, you get the password popup again, instead of it automatically getting access granted without asking.

---

### Post by pveurshout on 2010-11-01
edit: Nevermind. I was confused and later realized the contents of this post didn't make any sense..

---

