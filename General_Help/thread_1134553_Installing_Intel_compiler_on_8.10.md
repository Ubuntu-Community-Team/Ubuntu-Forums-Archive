---
title: "Installing Intel compiler on 8.10"
date: 2009-04-23
forum: General Help
---

### Post by whaler1 on 2009-04-23
I am trying to install Intel's non commercial compiler and everything was going fine until I received the message;
 
Missing Critical pre-requisite
-- missing system commands
-- 32-bit libraries not found
 
I found some guidelines for installation at
 
[http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)
 
which tell me I need libstdc++5 which I can't seem to find anywhere.
 
Does anyone have some insight to share.  As you can probably tell I am new to LINUX and any help is appreciated.

---

### Post by snova on 2009-04-23
Try installing the **libstdc++5** package.

---

### Post by whaler1 on 2009-04-23
I tried installing the package, this is what I entered;
 
"sudo get-apt install libstdc++5"
 
the message returned was;
 
E: Couldn't find package libstdc++5
 
I then looked through the Synaptic Package Manager and could not find the libstdc++5 package.  Is there something really obvious that I am missing.
 
Thanks

---

### Post by snova on 2009-04-23
> **whaler1 said:**
> I tried installing the package, this is what I entered;
 
"sudo get-apt install libstdc++5"
 
the message returned was;
 
E: Couldn't find package libstdc++5
 
I then looked through the Synaptic Package Manager and could not find the libstdc++5 package.  Is there something really obvious that I am missing.
 
Thanks

Open System -> Administration -> Software Sources, and check that the second box (Universe) is enabled; then try.

---

### Post by whaler1 on 2009-04-23
The box was originally checked but I tried it again...same problem.

---

