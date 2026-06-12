---
title: "Update Problem"
date: 2009-04-17
forum: General Help
---

### Post by ssdt on 2009-04-17
Please help me fix this error that I am getting when I try to install the updates available for my system.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

Thank you

---

### Post by kpkeerthi on 2009-04-17
Open a terminal and run this command
```
**sudo** dpkg --configure -a
```

---

### Post by Sef on 2009-04-17
> Open a terminal and run this command
 	Code:
 	**sudo** dpkg --configure -a 


To open the terminal:

Applications > Accessories > Terminal

---

### Post by ssdt on 2009-04-17
I got this message now. What do I do now?

Unable to find a precompiled module for the current kernel!               &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Without a suitable kernel module you will not be able to start any VMs.   &#9474; 
 &#9474; It is strongly recommended to compile a kernel module now. The kernel     &#9474; 
 &#9474; headers and the tools to build kernel modules (gcc, make, binutils, ...)  &#9474; 
 &#9474; are required. However if you know that a suitable kernel module already   &#9474; 
 &#9474; exists at another location, you might want to override the default by     &#9474; 
 &#9474; setting KDIR=<full_path_to_vboxdrv_module> in /etc/default/virtualbox.    &#9474; 
 &#9474; The compilation can also be done later by executing                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;   /etc/init.d/vboxdrv setup                                               &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; as root.

---

### Post by 3rdalbum on 2009-04-17
The message is saying "Virtualbox won't work unless you compile a new kernel module. You can compile it by typing 'sudo /etc/init.d/vboxdrv setup' at the terminal".

I imagine you have a textual "Ok" button at the bottom of the terminal, in which case you may need to press Tab to highlight it, and then Enter to click it.

---

### Post by ssdt on 2009-04-17
No i don't want to install anything just want to install any kind of programs that comes up. I want to delete virtualbox and then it would function. But I can't even go to sypnetec, then how do i delete virtualbox because it is causing a lot of problems.

---

### Post by ssdt on 2009-04-18
**Update:**
Problem fixed by Ubuntu forums. This topic can be closed down.

---

### Post by ClientSiman on 2009-04-19
> **ssdt said:**
> Please help me fix this error that I am getting when I try to install the updates available for my system.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

Thank you
I have the same problem.When i try to open Synaptic Package Manager i get the same error.I have tried ```
 sudo dpkg --configure -a 
```
but i got 
```
 dpkg: parse error, in file `/var/lib/dpkg/updates/0011' near line 1:
 newline in field name `padding'
```
I don't know what to do now,and i could use some help.
Thanks

---

