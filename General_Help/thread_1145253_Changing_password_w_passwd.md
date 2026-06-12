---
title: "Changing password w/ passwd"
date: 2009-05-01
forum: General Help
---

### Post by ranthal on 2009-05-01
I'm trying to change my password on a server at work because I have to change main corporate network password every few months and I try to keep it the same on the 10 different logins I have.

I really just use the same phrase every time except use capitals in different locations or replace letters with symbols (i.e. S with $) when I change it up since it's less to remember which leads me to the problem-I'm trying to use passwd to change my old password to the new one but it isn't allowing me to do so because they are too similar.

Is this to do with the passwd command itself or some other setting that the guy who set up the server put in place?  If it is the passwd command is there any option to override it?  I didn't see anything in the man page.

Yes, it's true that comparison is probably there for a good reason and I shouldn't use passwords so similar.  And yes, the guy who set up the server probably should have had the passwords sync up with the main corporate network but he didn't.

I could probably just set a dummy password that is completely different and then set it to my new one but now that I'm on this problem I want to see if there is a proper way to do it.

Thanks!

---

### Post by decoherence on 2009-05-01
It's probably not a function of the password command itself (depending on what system. i'll assume it's ubuntu.) It would probably be a function of libpam-cracklib.

There shouldn't be any way to get around this unless you're an admin in which case just reconfigure PAM so it no longer does this check. If you aren't the admin, trying to get around this may not be a good idea. If you succeed, let us know and we'll start worrying (lots of people depend on pam and cracklib being secure)

---

