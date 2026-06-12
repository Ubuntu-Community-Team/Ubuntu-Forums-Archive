---
title: "Ubuntu won't shut down"
date: 2009-03-27
forum: General Help
---

### Post by Jappsta on 2009-03-27
Hi all,
I've been having this problem for a while, starting from I think 8.04 and now in 9.04 as well. When I shut down/restart my laptop i see the 'splash' screen with the orange bar, but after that my laptop stops responding to everything but a hard reset. somehow ubuntu doesn't want to complete it's shutdown. Anyone have an idea to what might be causing this? 
Thanks,
Jappsta

---

### Post by glotz on 2009-03-27
If it's an older machine you might need to add **acpi=force** to the kernel line in /boot/grub/menu.lst.

---

### Post by Jappsta on 2009-03-27
I got it in september so i think acpi shouldn't be the problem but i'll check it out. Thanks for the reply.

---

