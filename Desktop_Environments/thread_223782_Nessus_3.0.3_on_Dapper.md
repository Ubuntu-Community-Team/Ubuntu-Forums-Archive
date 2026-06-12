---
title: "Nessus 3.0.3 on Dapper"
date: 2006-07-26
forum: Desktop Environments
---

### Post by endernet on 2006-07-26
When I install Nessus it complains about not being able to find libssl.so.0.9.7.  I did a find and couldn't find it, but I did find libssl.so.0.9.8.  Being relatively new to both Linux and Nessus, what can I do to get Nessus to use 0.9.8?

nessusd: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory

Thanks for your help

---

### Post by arpspoof on 2006-08-19
Hi! This is me trying to get nessus to work on dapper = ](*,) 

I've looked all over the net for something.  I even tried the older versions of nessus 3.0.1 & 3.0.2.

I can understand Tenable for going closed-source but this is how the community pays.

If anyone gets this to work, let us know!

---

### Post by omenix on 2006-09-25
ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so.0.9.7
ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.0.9.7

it works for me ;)

---

### Post by shahin on 2007-03-10
I can not get rid of this error:

nessusd: error while loading shared libraries: libnessus.so.3: cannot open shared object file: No such file or directory

Is this similar to the ssl error? Why does this happen please? How does making symbolic link fix the issue please?

---

