---
title: "problem getting kde??"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Digitallysick on 2005-06-12
i did the apt-get kde thing, and got this

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
i tried apt-get update and no updates avail??

---

### Post by Xian on 2005-06-12
What repos did the error message(s) pertain to? 
Try disabling those if not an official Ubuntu mirror and then update again.

---

### Post by Digitallysick on 2005-06-12
Here is the whole error, how do i fix?

[http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.0-0ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.0-0ubuntu10_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.4.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.4.0-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kuser_3.4.0-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kuser_3.4.0-0ubuntu1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-17_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-17_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.4.0-0ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.4.0-0ubuntu10_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/klaptopdaemon_3.4.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/klaptopdaemon_3.4.0-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kregexpeditor_3.4.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kregexpeditor_3.4.0-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdeutils_3.4.0-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdeutils_3.4.0-0ubuntu2_all.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by desdinova on 2005-06-12
[QUOTE=Digitallysick]Here is the whole error, how do i fix?

[http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.0-0ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.0-0ubuntu10_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.4.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.4.0-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kuser_3.4.0-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kuser_3.4.0-0ubuntu1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-17_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-17_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.4.0-0ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.4.0-0ubuntu10_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/klaptopdaemon_3.4.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/klaptopdaemon_3.4.0-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kregexpeditor_3.4.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kregexpeditor_3.4.0-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdeutils_3.4.0-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdeutils_3.4.0-0ubuntu2_all.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/QUOTE]
 us.archive.ubuntu.com has had some issues today.

---

### Post by Digitallysick on 2005-06-12
so is there anyway around it for now? i keep getting the error

---

### Post by Xian on 2005-06-12
Switch all instances of 'us.archive.ubuntu.com' in your /etc/apt/sources.list to 'archive.ubuntu.com', then do an 'apt-get update' session.

---

### Post by Digitallysick on 2005-06-12
that fixed it! thanks

---

### Post by beamo on 2005-07-07
I had the same MD5Sum mismatch error when trying to install something and I replaced us.archive.ubuntu.com with archive.ubuntu.com and it worked for me too. Do I need to switch the lines I changed back at some point or do I just forget about it?

---

