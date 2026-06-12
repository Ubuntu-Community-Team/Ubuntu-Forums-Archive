---
title: "Start ssh-agent at desktop login"
date: 2009-03-14
forum: Desktop Environments
---

### Post by shochatd on 2009-03-14
I would like to start ssh-agent at the point when a user logs into the (GNOME) desktop, followed by a call to ssh-add, which will cause the user to be prompted for his passphrase (using ssh-askpass). I know how to do all this, except for one thing: What script should I put it in so that it will happen during the desktop login process (so that all processes in that login session will have access to the agent)? In Sun Solaris with CDE, I put it in ~/.dtprofile and so what would be ideal would be a GNOME equivalent to that.
Thanks.
-- David

---

### Post by shochatd on 2009-03-15
Problem solved. ssh-agent is already started automatically via /etc/gdm/Xsession. Once I'm logged out the agent is gone (I think that's due to the way it was started). I put the command ssh-add in my ~/.xprofile. That then calls ssh-askpass to get the passphrase during login. 
It works.

---

