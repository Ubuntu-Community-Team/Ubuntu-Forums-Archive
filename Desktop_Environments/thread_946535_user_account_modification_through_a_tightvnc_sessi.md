---
title: "user account modification through a tightvnc session"
date: 2008-10-13
forum: Desktop Environments
---

### Post by csogilvie on 2008-10-13
Ubuntu 8.04 64-bit
running gnome in session:1 using tightvnc.

When I try to administer accounts (system/users and groups) the "unlock" button is grayed out...  Anybody know what might be the problem here?

If I log in from the console, I can happily modify my users and groups through gnome.

I would like to know how to get it working in session:1 through tightvnc because I have a co-located web-server with an identical setup...  And I can't modify user accounts through Gnome there either.

Everything of course works properly from the bash.

---

### Post by csogilvie on 2008-10-14
Nobody knows?

---

### Post by csogilvie on 2008-10-23
bump

---

### Post by Spitphire on 2008-10-26
I would also like to know solution to this problem. I have VNC session and unlock button is greyed out for Users and Groups..

-Spit

---

### Post by csogilvie on 2008-11-10
bump!  Somebody?  Anybody?  

It's hard(er) to administer a co-located server without this!

Please?

---

### Post by csogilvie on 2008-11-14
I read somewhere this was a "policy kit" somethin' or other...

Anybody have any ideas?

---

### Post by csogilvie on 2008-12-03
somebody has to know the answer to this!!!  HELP!

---

### Post by csogilvie on 2008-12-11
nobody knows?!?!?  ARRRRRRGGGGGHHHHH!

help!

---

### Post by csogilvie on 2009-02-06
I have discovered the soloution myself.

You have to adjust your "authorizations" from the console to permit these actions.

As I had suspected this is indeed handled by the policy kit.

---

