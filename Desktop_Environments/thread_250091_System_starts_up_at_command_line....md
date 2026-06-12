---
title: "System starts up at command line..."
date: 2006-09-03
forum: Desktop Environments
---

### Post by puppy on 2006-09-03
Hi everyone, I've been spending the day installing Ubuntu Dapper (NVidia graphics card) but after my second restart, the system started and dumped me at the command line. Logging in and typing "startx" works fine, and gets me into the UI, but obviously I would like the system to load up the graphical system from the start. Can anyone advise what file entry to change to tell Ubuntu to do this please (and maybe tell me what it is I broke :o )

Many thanks for any advice

Pups

---

### Post by croak77 on 2006-09-03
Do you have gdm, kdm, or xdm installed? After you login, try; sudo /etc/init.d/gdm start (change gdm to kdm or xdm). And see if it does start or if there are any errors.

---

### Post by kh4nh on 2006-09-03
look for these lines

# The default runlevel.
id:[NUMBER]:initdefault:

in the file /etc/inittab, change [NUMBER] to 2-5. Cheers

---

