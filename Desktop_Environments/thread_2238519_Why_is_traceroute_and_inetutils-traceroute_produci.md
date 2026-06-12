---
title: "Why is traceroute and inetutils-traceroute producing this warning on install?"
date: 2014-08-08
forum: Desktop Environments
---

### Post by MakOwner on 2014-08-08
sudo apt-get install inetutils-traceroute
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  inetutils-traceroute
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.0 kB of archives.
After this operation, 206 kB of additional disk space will be used.
**WARNING: The following packages cannot be authenticated!**
  inetutils-traceroute
Install these packages without verification [y/N]?

I get this on a 64 bit desktop installation, but not on 32 or 64 bit versions of server installations.
Do I have issues or is this expected?

---

### Post by Lars Noodén on 2014-08-08
Did you refresh the package index first?

```

sudo apt-get update

```

---

### Post by MakOwner on 2014-08-08
yup.
Always.  

91.189.88.149 80 is reporting "404 Not Found" -- is it down again and that's whats causing it?

---

### Post by Lars Noodén on 2014-08-08
Can you switch repositories to another one that is nearby and try it?

---

### Post by SeijiSensei on 2014-08-08
One of the first things I do on any new installation is switch to using a mirror. Usually I choose a nearby university since they have big pipes.  I'm using mirrors.mit.edu at the moment.

---

