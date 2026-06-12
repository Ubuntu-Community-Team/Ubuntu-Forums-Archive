---
title: "Dual boot - Ubuntu and Mythbuntu - how to remove one?"
date: 2009-06-14
forum: General Help
---

### Post by BB2008 on 2009-06-14
Hi All:

This is my situation:

I have a machine that has Ubuntu (upgraded to 9.04) loaded on it since August 2008. Recently, I wanted to try out mythbuntu, so I installed that on the same machine in a dual boot configuration.

My question:

I am done with my trial of mythbuntu and want to remove it from my machine. What is the way to do that? Please help.

Thanks in advance.

---

### Post by ajgreeny on 2009-06-14
If it is a completely separate installation rather than just an install of myth on top of ubuntu, you can just delete the mythbuntu partition using gparted.  You will need to reinstall the grub from your original ubuntu, as no doubt mythbuntu took over grub when you installed that, but you can either do that first with the live ubuntu CD or after getting rid of mythbuntu.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by BB2008 on 2009-06-14
Thanks ajgreeny. I will try this and get back if I get into any issues.

---

