---
title: "remote CD-rROM burning"
date: 2009-06-14
forum: General Help
---

### Post by sandyd on 2009-06-14
I currently do not have a CD/DVD burner on my comp. Im not planning to buy one.

The family computer downstairs has two (one cd, one DVD/CD). would it be possible to make it so that I can open up a cd burning program up here, and remotely burn the cd?

Both computers are running Ubuntu 9.04.

---

### Post by jimv on 2009-06-14
If the one downstairs has two burners, why not just swap one with one from your computer?

---

### Post by sandyd on 2009-06-15
> **jimv said:**
> If the one downstairs has two burners, why not just swap one with one from your computer?

i don't have space for one. 

The computer I work on is actually a server thats acting as a VPN/Gateway, and aparently, it doesn't have room to install one

---

### Post by boof1988 on 2009-06-15
One option (among many) is to use [SSH](http://en.wikipedia.org/wiki/Ssh) (or your favorite remote shell) to access the other machine.  Then you can use [cdrecord](http://en.wikipedia.org/wiki/Cdrecord) (or your favorite CLI/GUI CD burning software) to burn the cd in the remote computer's drive.

Hope this helps...

---

### Post by sandyd on 2009-06-15
im thinking of something more like mounting the remote cdrom drive in samba and pointing the burning program towards it, but i know that wouldn't work.

---

