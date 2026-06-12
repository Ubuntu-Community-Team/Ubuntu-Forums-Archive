---
title: "ssh keys not working in ubuntu?"
date: 2006-01-11
forum: General Help
---

### Post by dogas on 2006-01-11
Hi guys.. I have a strange problem ever since installing ubuntu a week ago.  It seems that none of my ssh keys are able to load, claiming that I'm using an invalid passphrase.  Even using the same exact key that works on any other system, once I try to ssh-add it in ubuntu, I get the 'invalid passphrase'.  

Is ubuntu's openssh package different in any way?  I've had to resort to turning on password-based authentication on my server, which sucks.

Thanks in advance for any help!

---

### Post by dogas on 2006-01-11
fixed.  I did not have my keys chmodded to 700.  Once I did that, everything works fine.

---

