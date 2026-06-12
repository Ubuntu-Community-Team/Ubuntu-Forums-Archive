---
title: "APT-GET and Synaptic error"
date: 2005-07-11
forum: Desktop Environments
---

### Post by chrisndebb on 2005-07-11
When I try to get a program by apt-get or Synaptic I often get an error message like this but not always the same packages in error. 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)
  MD5Sum mismatch

But every one I get has the same "MD5Sum mismatch" at the end of it. 
Any ideas?
Chris

---

### Post by emperor on 2005-07-11
[QUOTE=chrisndebb]When I try to get a program by apt-get or Synaptic I often get an error message like this but not always the same packages in error. 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb")
  MD5Sum mismatch

But every one I get has the same "MD5Sum mismatch" at the end of it. 
Any ideas?
Chris[/QUOTE]

edit /etc/apt/sources.list and remove the "us." on all repo entries.

---

