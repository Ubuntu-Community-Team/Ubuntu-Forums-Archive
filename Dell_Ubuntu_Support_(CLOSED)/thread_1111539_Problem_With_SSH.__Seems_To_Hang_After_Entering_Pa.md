---
title: "Problem With SSH.  Seems To Hang After Entering Passwd"
date: 2009-03-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jersey Legend on 2009-03-30
Whats going on people.  I received my dell mini 9 w/ ubuntu a few days ago.  I've been trying to ssh to my school server through a wireless connection, which in fact does because it does ask me for my password.  But once I enter my password, it goes to the next line and the  cursor just flashes there as if its waiting for something.


A few weeks ago, I partitioned my desktop HD and make a new install of ubuntu, and just about everything works correctly, even the ssh.

Any ideas what it might be? It's annoying me because I want to ssh to the cs server so I can do my work around my dorm, and not necessarily in my room at all times.

---

### Post by Jersey Legend on 2009-03-30
and I have a feeling it has to do with it being the wireless connection.

---

### Post by Jersey Legend on 2009-03-30
never mind, I have found the answer

I'll post it here just in case others have the same problem

add this to the end of this file /etc/network/if-pre-up.d/wireless-tools


if there is a mod out there, you can close this.

/sbin/iwpriv eth1 set_vlanmode 0

---

