---
title: "[SOLVED] Cannot adminster users"
date: 2008-06-29
forum: Desktop Environments
---

### Post by prshah on 2008-06-29
Hello:

Ever since installing ubuntu-hardy (upgraded from Fiesty-Gutsy) I do not have access to properties of other users in users-admin.

When I launch System-Administration-Users & Groups, I am asked for root password, then list of local users comes up, and "Add User", etc buttons are greyed out. Even properties can only be opened for my (current) username. I have all admin rights.

There is an "Unlock" button on the bottom right side of the window, but that is grayed out as well.

I have tried launching users-admin as sudo, to no avail.

I have tried playing around with the policyKit settings, but they fly over my head, I've no idea what I'm doing there.

Screenshot attached for clarity.

Any suggestions/solutions/workarounds?

---

### Post by aysiu on 2008-06-29
Maybe make sure you're in the *admin* group (by the way, there shouldn't be a root password, unless you set one - you should be prompted for your user password):
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by prshah on 2008-06-29
> **aysiu said:**
> Maybe make sure you're in the *admin* group (by the way, there shouldn't be a root password, unless you set one - you should be prompted for your user password):
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

No there is no root password; I just wanted viewers to know that I'm accessing users-admin with sudo (root) privileges. 

I'm already member of "admin" group:```

Sun Jun 29 23:17:31 ~:$ groups username
username adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin admin netdev powerdev vboxusers sambashare

```

Any further ideas? How do I unlock/enable the "unlock" button?

---

### Post by sisco311 on 2008-06-29
Try to run users-admin, from a terminal, without sudo. Maybe is a conflict between sudo/gksudo and policyKit.

---

### Post by prshah on 2008-06-29
> **sisco311 said:**
> Try to run users-admin, without sudo. Maybe is a conflict between sudo/gksudo and policyKit.
__________________
Enter any 11-digit prime number to continue... 

99999999977 (Here's your 11-digit prime number as requested)

Unbelievable. It worked. Thanks. However the unlock button is still grayed out; but no matter I can make what changes I want. Weird.

---

### Post by linuxn00b84 on 2008-12-19
*bump* I also have this problem and have tried those solutions (and several others) to no avail. Any other ideas on why the button would be grayed in the first place?

---

### Post by Ghilteras on 2009-01-30
sorry to bump this thread, but it's not solved at all, i made a search and there are at least 10 threads about bugged policykit on hardy/intrepid, none of them can solve the problem.

i had to use sudo polkit-gnome-authorization and manually grant my user to manage system as workaround but the unlock button is still grayed out.

it's not a solution because even if i can manage my system setting this way i want to understand why i cannot use my unlock button, is it a policykit problem? because i tried reinstalling it to no avail

regards

---

