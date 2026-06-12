---
title: "Dell Ubuntu 8.04 Linux-headers For VMware kernel modules compile"
date: 2009-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by frenchrh on 2009-07-31
[LEFT][LEFT][FONT=Times]      I just got a Dell Mini 10 running Dell Ubuntu 8.04. When I install VMware Player 2.5, it installs from the bundle with no problem But upon first running VMware Player, as it automatically builds the necessary kernel modules, it fails on the Dell Mini 10 due to not having the kernel sources (called linux-headers in Ubuntu land). The kernel has been updated in a system update to 2.6.30 (I think) and its the Dell "lpia", and apparently the default Dell package repository doesn't have the appropriate kernel sources,that exactly match the installed lpia kernel.[/FONT][/LEFT]
[/LEFT]
    [LEFT][LEFT][FONT=Times]So how do other people handle this problem, so they can run the free VMware Player?[/FONT][/LEFT]
[/LEFT]
    [LEFT][LEFT][FONT=Times]Thanks for your help[/FONT][/LEFT]
[/LEFT]

---

### Post by snowpine on 2009-07-31
The terminal command 'uname -a' will tell you which kernel you're running, and you should be able to install the appropriate headers using Synaptic.

---

### Post by frenchrh on 2009-07-31
I agree in theory with what you say.  But Dell 8.04 Ubunutu uses the lpia kernel, and in the lpia kernel ubuntu repository for Dell, they don't have the linux headers for all the kernels.  So upgrading to the latest lpia kernel  (something like .28) means that there aren't the headers that match .28 kernel version.  If Dell used the generic kernel instead of the lpia kernel, then I don't think this would be an issue. but apparently the lpia repositories, like the Dell 8.04 one, are very short on packages.

so how do i do it for this version, that lpia dell one?

Roger

---

### Post by snowpine on 2009-07-31
What is the output of 'uname -a' ? You probably have 2.6.24 if you're running 8.04. If Dell does not provide the correct headers, that is disappointing.

I personally do not use lpia on my Dell Mini; sorry I can't be of further assistance.

---

