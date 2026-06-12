---
title: "Hide computer name"
date: 2009-01-14
forum: General Help
---

### Post by just_linux on 2009-01-14
Hi, 
I want to remove my computer name and my user from my terminal!!
it is so stupid !!! 
so instead of joseph@laptop:~/Desktop$ I get :~/Desktop$:popcorn:
Thanks a lot

---

### Post by easybake on 2009-01-15
Is this what you are looking for?

[http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm]("http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm")

---

### Post by blakeurmos on 2010-12-05
Edit your .bashrc file located in your home directory
```
gedit ~/.bashrc
```

Look for the PS1 variable probably looks like
```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

Remove this:
```
\u@\h:
```

The \u is username the \h is hostname. You will be removing *username@hostname:* from your bash prompt. I know this is almost 2 years later, but I hope it helps someone.

---

