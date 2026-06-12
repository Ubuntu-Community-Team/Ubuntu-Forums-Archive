---
title: "virtualbox XP guest can't see shared folder"
date: 2009-04-23
forum: General Help
---

### Post by cornstalk on 2009-04-23
The host is Ubuntu 8.10 64-bit, the guest is Windows XP Pro 32-bit.  I created a virtual machine with virtualbox guest utilities already installed (but not virtualbox guest addition module source).  I created directory winshare in my home directory and defined it as shared using virtualbox.  I powered up a dos command line and went "net use x: \\vboxsvr\winshare".  The dos reply was System Error 53 - network path not recognized.

I have since installed virtualbox gues addition module source, but the symptom persists.  So far I have no way to share files between the guest and the host.  Any help would be much appreciated.

Thanks in advance, cornstalk. 

P.S. The virtual Windows machine otherwise works fine.

---

