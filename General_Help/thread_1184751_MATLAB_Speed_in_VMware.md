---
title: "MATLAB Speed in VMware"
date: 2009-06-11
forum: General Help
---

### Post by amazurenko on 2009-06-11
Hello, I am running Ubuntu 9.04 on a Lenovo T61. I have been having many issues with the linux version of MATLAB provided by my school, but I need it to do some heavy number crunching. 

I was wondering how well does MATLAB run in VMWare?

Thank you,

amazurenko

---

### Post by andersbk on 2009-06-11
> **amazurenko said:**
> Hello, I am running Ubuntu 9.04 on a Lenovo T61. I have been having many issues with the linux version of MATLAB provided by my school, but I need it to do some heavy number crunching. 

I was wondering how well does MATLAB run in VMWare?

Thank you,

amazurenko

Works quite well. Especially if you use VMWare workstation, or any other KVM compatible virtualizer. That is, your CPU has to support KVM and the tool doing the virtualization has to support KVM. Jaunty has support for kvm.

[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)

.

---

