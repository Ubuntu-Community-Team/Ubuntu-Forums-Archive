---
title: "no local group credentials logging in with gdm"
date: 2009-09-11
forum: Desktop Environments
---

### Post by gmoore777 on 2009-09-11
Symptom: (HardyHeron with LikeWise-Open)
User logs into Console. Opens up a terminal window. Executes `id`.
It shows that user is in all the associated Windows groups but not in any of the local Linux groups.

WorkAround:
In same window, user executes `su DOMAIN\first.last`, then `id`, it will show user is in the appropriate Windows and Linux groups.

Problem does not occur if user `ssh` into the machine.

It happens with 3 users on each of their machines.

I had 2 of those users log into my Console window and the problem does not happen.

This problem does not happen with 10 or so other people
on their own machine.

All machines are built identical to eachother.
(but obviously something is different)

I've removed all the cache files for likewise-open under /var/lib/likewise-open.
I've even changed the /etc/pam.d/su file to make it look like
the /etc/pam.d/gdm file to see if I could cause the problem by
just `su`-ing but that didn't work.

So what I have is an ActiveDirectory-related problem, associated with gdm (the GNOME console) and associated with a specific machine(or Home Directory) specific.

Is there a way I can control GDM in such a way that it's login shell has the group credentials from both Linux and ActiveDirectory?


Does GDM grab prevoius credentials from the user's home directory or somewhere else? and `su` is not using any cache?

Help?

---

