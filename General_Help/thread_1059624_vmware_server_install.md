---
title: "vmware server install"
date: 2009-02-03
forum: General Help
---

### Post by jblinuser on 2009-02-03
im not too sure if this is the right place for this question but this is where im putting it. i ran through this install how to for vmware server and i got to a point where it was installed and then i had to configure it. it said that it needed a vmmon module and that it was unable to build the vmmon module. can anyone help me with this?

this is the how to that i used....[http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware+server+install](http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware+server+install)

if anyone needs to see the output that i got in the terminal i can post that as well.

---

### Post by HermanAB on 2009-02-04
That means that you haven't installed the kernel development header files for your running kernel.

I always solve the problem by installing the kernel source and rebuilding and installing the kernel.  That process ensures that everything is configured properly, after which VMware will install without any trouble.

Cheers,

Herman

---

