---
title: "Installing VMWare Tools"
date: 2007-07-29
forum: Dell  Ubuntu Support
---

### Post by dzldriver on 2007-07-29
Running on VMWare 5.5.1 installed in a Dell Inspiron 8200.

Ok. So here is where I am at. I have had to install Ubuntu 7.04 Feisty Fawn in a virtual machine so as not to upset the domestic balance of my house. Trying to install VMWare tools is proving to be a challenge though. Everything is going great until I get to the point where the install script asks for the location of the running kernel. I used 'uname -r' to find out that I am running 2.6.20-16-generic kernel. When the machine asks me for the location I tell it and the following is the response that I get in the terminal window.
================================================== =========
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-16-generic). Even if the module were to
compile successfully, it would not load into the running kernel.

================================================== =========

Does anyone know where I need to go from here. I have been more or less forced away from the Linux world for the last two years. The last OS that I tried to convert my family to was Mandrake 10.0. I was not successful.

Hoping someone can help me.
dzl

---

### Post by plewisfdx on 2007-07-29
I'm not familiar with VMWare but it appears to be asking you for the *location* of the kernel, not the kernel version.  The location would be: /boot/vmlinuz-2.6.20-15-generic

I apologize if this is what you typed, just worth a try if you entered something else.

---

### Post by dzldriver on 2007-07-29
What the install script is asking me for is the location of the header files for the kernel that I am running.  The default in the install script is /usr/src/linux/include.  With Ubuntu I have changed it to /usr/src/linux-headers-2.6.20-16-general/include. and the message as pasted above is what is returned from the system.

---

### Post by garrison on 2007-08-09
> **dzldriver said:**
> 
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-16-generic). Even if the module were to
compile successfully, it would not load into the running kernel.
l

vmware-config.pl is looxing at [COLOR="Indigo"]/usr/src/linux/include/linux/version.h[/COLOR] and not finding ```
#define UTS_RELEASE "2.6.20-16-generic"
``` because it's in [COLOR="Indigo"]utsrelease.h[/COLOR]

I don't know why UTS_RELEASE was moved to it's own file but a number of applications are choking on this. The quick fix is to simply prepend the UTS_RELEASE line from utsrelease.h to version.h

---

### Post by Phil Baxter Jr. on 2007-08-09
> **garrison said:**
> vmware-config.pl is looxing at [COLOR="Indigo"]/usr/src/linux/include/linux/version.h[/COLOR] and not finding ```
#define UTS_RELEASE "2.6.20-16-generic"
``` because it's in [COLOR="Indigo"]utsrelease.h[/COLOR]

I don't know why UTS_RELEASE was moved to it's own file but a number of applications are choking on this. The quick fix is to simply prepend the UTS_RELEASE line from utsrelease.h to version.h

Sounds like you might be able to help me.  Stuck on trying to get the
VMWare Tool .gz to install.  Problems figuring out where to expand .gz files to, as not recognized location when expanding.

Realize a difficult question, for virtual operation in IBM T-22, Windows XP-pro with ubuntu 7.04.

Thanks,   Phil, Sonoma CA

---

### Post by rrinker on 2007-08-09
I HAD 7.04 working great in a  VM on my work laptop. Actually, it started at 6.10 and then I upgraded to 7.04. Then I made the mistake of installing the VMWare Tools, and I no longer have any network connectivity from the VM. Not sure what I did but I had no problem getting it to compile. It just broke my networking.

---

