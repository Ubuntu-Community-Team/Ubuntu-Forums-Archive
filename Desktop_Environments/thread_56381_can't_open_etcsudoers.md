---
title: "can't open /etc/sudoers"
date: 2005-08-12
forum: Desktop Environments
---

### Post by homerglemkin on 2005-08-12
I was doing an apt-get upgrade and when it was done sudo did not work anymore.
What I get is the following:
sudo: can't open /etc/sudoers: Success
I only have had this show up on one machine, that I just installed using the Ubuntu CD s that were shipped to me.
Any help would be appreciated.
Thanks,
Homer

Hoary 5.04
kernel 2.6.10-5-386

---

### Post by shakin on 2005-08-12
[QUOTE=homerglemkin]I was doing an apt-get upgrade and when it was done sudo did not work anymore.
What I get is the following:
sudo: can't open /etc/sudoers: Success
I only have had this show up on one machine, that I just installed using the Ubuntu CD s that were shipped to me.
Any help would be appreciated.
Thanks,
Homer

Hoary 5.04
kernel 2.6.10-5-386[/QUOTE]
 Any other error when you try to run sudo? If the permissions on /etc/sudoers is wrong it won't run, so check that. You can probably use a livecd to fix that. FWIW, I always enable the root account just so I can fix any problems with sudo.

---

### Post by homerglemkin on 2005-08-12
Nope just that, so I'm thinking it's a reinstall then. I just got Ubuntu installed with the server boot option and the upgrade was its first.

---

### Post by az on 2005-08-12
[QUOTE=shakin]Any other error when you try to run sudo? If the permissions on /etc/sudoers is wrong it won't run, so check that. You can probably use a livecd to fix that. FWIW, I always enable the root account just so I can fix any problems with sudo.[/QUOTE]
You just have to boot into recovery mode to be root.  Then do
nano /etc/sudoers
to fix the sudoers file (add your user there)

WHat did you dist-upgrade to that broke sudo?  Did you have any non-ubuntu repositories?

---

