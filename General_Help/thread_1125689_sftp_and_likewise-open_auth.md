---
title: "sftp and likewise-open auth"
date: 2009-04-14
forum: General Help
---

### Post by ronin2307 on 2009-04-14
Hi,

I have managed to set up openssh and likewise on my machine. for sftp I would like to be able to only use local accounts to connect to this machine. However at this point because I am using likewise-open as well, all domain members can use their domain credentials to log in to my ubuntu machine. to make the matters worse they are not chrooted either.

is there any way to set this up so that for sftp only local account(s) would be allowed and that I can still log in locally to my ubuntu machine with my domain credentials but with sftp?

thanks

PS: I am using PAM with openssh
PSS: Or can I chroot domain users as well somehow?

---

