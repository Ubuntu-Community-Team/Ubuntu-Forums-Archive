---
title: "How to prevent KDE from restoring previous session"
date: 2006-07-21
forum: Desktop Environments
---

### Post by mad_alfred on 2006-07-21
Hi everyone!
 
Everytime a session starts KDE restores the previous one. How can i disable this function?

thanx in advance,
chris

---

### Post by mad_alfred on 2006-07-21
sorry if i haven't been precise in my previous post, i want to disable this function from console.

---

### Post by vigleik on 2006-07-21
> **mad_alfred said:**
> sorry if i haven't been precise in my previous post, i want to disable this function from console.

Why did you have to make the question so much harder? Normally you would do this from the control center, under session manager. Maybe you can use kconf_update. Otherwise I bet you could edit one of the files in .kde/share/config/ by hand, though I don't know which one sets the restore to true or false.

Vigleik

---

### Post by NeoChaosX on 2006-07-21
System Settings > KDE Components > Session Manager > Select "Start with an empty session"

---

### Post by Ardrias on 2008-05-23
Time for a big old BUMP!

I too want to know how to disable the behaviour from commandline. Any tips?

---

