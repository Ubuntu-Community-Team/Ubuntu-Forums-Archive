---
title: "problem logging into gnome-session-flashback on fresh installation"
date: 2022-10-15
forum: Desktop Environments
---

### Post by jerryferry on 2022-10-15
Been using gnome-session-flashback for a long time, and after a re-installation  today it wont recognise the password. 

I can log into gnome, but select metacity flashbak and it just bounces me back to log prompt.

Hope somebody can shed some light on this, gonna try deleting all hidden files, will post back if that fixes it.

Ubuntu 22.04, i7, 16 gig ram, nvidia graphics. separate home partition.

---

### Post by jerryferry on 2022-10-15
Deleted, hidden files, still cant log into metacity.

---

### Post by #&amp;thj^% on 2022-10-15
is "export DISPLAY=:0" set in ~/.bashrc,?

---

### Post by ajgreeny on 2022-10-15
> **jerryferry said:**
> Deleted, hidden files, still cant log into metacity.
What do you mean by this?

What did you delete?

---

### Post by grahammechanical on 2022-10-16
Please give some information about your system and this re-install? Was this a fresh install of Ubuntu 22.04 with a fresh install of Gnome-session-flashback afterwards? Does this installation have a separate /home partition? Did you re-install by putting Ubuntu into the /root partition and not formatting the /home partition. In this way we do not loose our configuration files. But is gnome-session-flashback installed?

Regards

---

### Post by jerryferry on 2022-10-17
deleted everything except my data-files on home partition, usually preferred to leave some configuration files to keep some of the settings but was running out of ideas. found a solution elsewhere on web. ctrl/alt/f3, login at terminal. perform updates. turned out it was a login loop that for some reason vanilla gnome was immune from. glitch could be my configuration or motherboard. the terminal login/update broke the loop. also tried some ubuntu 22.04 variants, they had the same boot loop problem.

---

### Post by jerryferry on 2022-10-17
yes to all of above.

---

### Post by #&amp;thj^% on 2022-10-17
> **jerryferry said:**
> yes to all of above.

If yes to this>>>" **DISPLAY=:0" set in ~/.bashrc**," then remove it.  and try again

---

