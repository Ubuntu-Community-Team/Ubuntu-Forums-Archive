---
title: "using kubuntu as a host for vmware"
date: 2005-04-25
forum: Desktop Environments
---

### Post by procyon on 2005-04-25
i just want to know whether kubuntu can act as a host for vmware. thank you

---

### Post by Firetech on 2005-04-25
I use kubuntu and vmware, and it works fine.
You have to compile your own kernel though. (As far as I've tried, the linux-headers-[version] package doesn't help.)

---

### Post by mlmurray on 2005-04-25
I'm running VMWARE on Kubuntu and I didn't need to compile a new kernel (Did have to on Mepis and Fedora).  All I did was install the kernel-headers package.

You do need to either specify the location of the include files during Vmware installation or (like I did) make a link as follows;

ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux

Worked like a charm for me  :)

---

### Post by Firetech on 2005-04-26
[QUOTE=mlmurray]I'm running VMWARE on Kubuntu and I didn't need to compile a new kernel (Did have to on Mepis and Fedora).  All I did was install the kernel-headers package.

You do need to either specify the location of the include files during Vmware installation or (like I did) make a link as follows;

ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux

Worked like a charm for me  :)[/QUOTE]
 Which version of vmware are you running? My vmware-config.pl file whines at my source folder not containing some directories that are created upon compiling.
I'm running 5.0 (didn't work with the last 4.x.x version either).

---

### Post by mlmurray on 2005-04-27
I'm running VMWare 4.5.2.  Don't know why it isn't working for you.  The link I pointed out was specific to the kernel I was running so the link command would actually be:


ln -s /usr/src/linux-headers-*whatever-kernel-version-you-have* /usr/src/linux

apologies if you already knew that.  

The other thing you could try is just input the specific path to your header files when you run 'vmware-config.pl' and it asks for the location of the include files.

-Mark

---

