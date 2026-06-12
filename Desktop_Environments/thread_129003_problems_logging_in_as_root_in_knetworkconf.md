---
title: "problems logging in as root in knetworkconf"
date: 2006-02-12
forum: Desktop Environments
---

### Post by klett on 2006-02-12
Hi,

A few days ago I had to reinstall Kubuntu. 

I had noticed that sometimes my laptop got too hot and Ksysguard reported that the cpu was working at 90%. I googled a bit nad found a way to find out which process was eating up my cpu. 

top reported the process was perl.
Running ps auwx | grep perl I obtained:
perl usr/share/apps/knetworkconf/backends/network-conf --set
 
So everytime I ran knetworkconf to change my dns, I checked what was happening with top. Sometimes perl was eating my cpu and sometimes not.

One day I started my computer and got a grub prompt. I decided to reinstall Kubuntu, because I didn't know how to fix it any other way.

Now, I have problems again with knetworkconf. I cannot log in as root. I tried to run the package manager and I've received an error message saying that I should  check whether dcopserver is working. Authentication hadn't been possible.

Is there a known bug in kde 3.4.3? Or in knetworkconf 0.6.1?

---

