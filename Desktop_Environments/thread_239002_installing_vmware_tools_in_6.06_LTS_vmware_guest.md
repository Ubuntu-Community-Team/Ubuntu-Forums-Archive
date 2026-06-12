---
title: "installing vmware tools in 6.06 LTS vmware guest"
date: 2006-08-18
forum: Desktop Environments
---

### Post by dsbiker on 2006-08-18
I am new to all this.  I am trying to install VMWare tools in a Ubuntu 6.06 VMWare guest OS. When running vmware-install.pl I get the following message regarding the kernel header files:

------------
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/include

The header files in /usr/include are generally for C libraries, not for the
running kernel. If you do not have kernel header files in your /usr/src
directory, you probably do not have the kernel-source package installed. Are
you sure that /usr/include contains the header files associated with your
running kernel? [no] yes

The directory of kernel headers (version 2.6.11) does not match your running
kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.
------------

How do I get and install the proper C header files?  All successful tips appreciated.  Thanks.

---

### Post by ifishfortorque on 2006-08-18
You might try 

```
sudo apt-get install linux-headers linux-source
```

and see if it gets anywhere.

---

### Post by mdelorme on 2006-08-18
You'll also need to install the appropriate compilation tools.

```
sudo apt-get install build-essential
```

Just in case you still have complaints about the header files, also try

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by dsbiker on 2006-08-18
Problem solved.  Thanks to both of you.

The real key was: sudo apt-get install linux-headers-$(uname -r)

I had already figured it out.  But that command would have been the "easy" way.

Thanks.  This is a very responsive forum!

---

