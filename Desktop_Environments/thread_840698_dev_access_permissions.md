---
title: "/dev access permissions"
date: 2008-06-25
forum: Desktop Environments
---

### Post by nrundle on 2008-06-25
I am having trouble getting onto my desktop environment.  The gnome login screen comes up and if I try to login I get an error about unable to create child process, the log shows "PRNG not seeded"

If I try failsafe-terminal I get the error "not enough ptys".

If I Alt-Ctrl-F2 and login I get the "bash: /dev/null: Permission denied"

If I then ctrl-c and "sudo chmod a+rw /dev/*" I can get everything to work fine and login to my desktop.  This system was working fine before and there was a power outage while it was on and then this started happening.  

Any ideas what is going on with the permissions here?  I know that I shouldn't be doing the chmod a+rw on the entire dev directory so something with gdm must be messed up and it isn't getting the right permissions.  Where should I look for the problem?

---

