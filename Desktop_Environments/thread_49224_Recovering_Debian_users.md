---
title: "Recovering Debian users"
date: 2005-07-15
forum: Desktop Environments
---

### Post by academician on 2005-07-15
Hello.  I am attempting to recover a Debian 'testing' installation onto an Ubuntu installation, and right now I am setting up the users.  Should the only thing I have to do be to copy over the users from passwd and shadow, and copy the home directories over?  Or is there something else I need to do (ie, for PAM)?  Forgive me, as I am quite new to Ubuntu, but due to a certain chain of events this is the situation I find myself in :-P

It looks wonderful so far, kudos to the Ubuntu community.

---

### Post by academician on 2005-07-15
Ooops, it appears I posted this in the wrong forum by mistake!  I feel like a newb  :-#  I thought I was in the Installation forum.  If some mod can move it for me, it would be much appreciated.

---

### Post by academician on 2005-07-15
I seem to have figured it out on my own.  :) 

I did end up copying users out of the old /etc/passwd into the new one, as well as /etc/shadow.  I also copied over groups from /etc/group.  Then I copied /var/spool/mail files, set up postfix roughly the same way, etc. etc.  And it's almost all working now, thankfully.

---

