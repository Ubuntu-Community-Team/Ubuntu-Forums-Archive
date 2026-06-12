---
title: "Timevault: Cannot install 'python2.5-dev'"
date: 2008-07-31
forum: Desktop Environments
---

### Post by gmalac on 2008-07-31
Hi,
I am under ubuntu 8.04 and would like to install timevault as my backup solution.
Timevault is not on the repositories so I use gdeb (double cliking on their site) but it won't install for the message above.
Going to synaptic and trying to install python2-5-dev I got this error message:
QUOTE:
python2.5-dev:
 Depend : python2.5 (=2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 must be installed
UNQUOTE:
Any idea?
Thanks
Guy

---

### Post by FatDave on 2008-07-31
I was having the exact same problem and with much searching found [this thread]("https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/244110"). Long story short, you can manually install python2.5-dev from deb files. Get them here:

i386 - [https://launchpad.net/ubuntu/hardy/i386/python2.5-dev/2.5.2-2ubuntu5](https://launchpad.net/ubuntu/hardy/i386/python2.5-dev/2.5.2-2ubuntu5)
amd64 - [https://launchpad.net/ubuntu/hardy/amd64/python2.5-dev/2.5.2-2ubuntu5](https://launchpad.net/ubuntu/hardy/amd64/python2.5-dev/2.5.2-2ubuntu5)

---

### Post by Ihaveaproblem on 2008-08-05
Thank you FatDave, I had problem with python2.5-dev AMD64! Now ok!
:)

---

