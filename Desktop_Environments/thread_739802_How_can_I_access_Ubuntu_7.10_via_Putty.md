---
title: "How can I access Ubuntu 7.10 via Putty"
date: 2008-03-30
forum: Desktop Environments
---

### Post by rats54 on 2008-03-30
Hi,

I have just installed Ubuntu 7.10 Gutsy Gibbon following The Perfect Desktop- Ubuntu 7.10 "Gutsy Gibbon" guide by Oliver Meter.  Now I want to Putty into GG from a Windows box.  When I try to apt-get install openssh-server I get a message: Package is not available.

How/where can I get the openssh-server package for GG?  

I have been able to apt-get install openssh-server on Ubuntu 7.10 Server with no problem.  I can Putty into the GG server with no problem.

Does the fact the desktop has Gnome running on it and the server is strictly CLI have anything to do with this problem?

Thanks,

---

### Post by googlah on 2008-03-30
Hey there,

It shouldn't be. Running GNOME or plain CLI shouldn't be the cause. Have you looked into your sources.lst file on your GG GNOME machine? Try uncomment everything you see, and run a "apt-get update". Then, run "apt-get install openssh-server". That SHOULD work.

Peace out

---

