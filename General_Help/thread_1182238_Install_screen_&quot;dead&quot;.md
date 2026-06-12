---
title: "Install screen &quot;dead&quot;"
date: 2009-06-08
forum: General Help
---

### Post by Ocke on 2009-06-08
Hi folks. ):P

Installing Ubuntu in a partition on a vista laptop, from a CD. When I come to the main installation screen I can´t make any choices, since nothing happens when I press enter. 
Have also tried "Wubi" in vista, but nothing happens. Downloaded from 3 seperate sites but still get the same results. I have not had this problem before and if someone has a solution I would be more then thankfull. 

I have the correct version 9.04 for Intel. Not an expert on Ubuntu and Unix btw, so please bare with me :p

Cheers.

---

### Post by ronparent on 2009-06-08
Have you tried it out by running the live cd? Does it load and run with no freeze? If no, then try hitting F6 - options at the first menu screen when booting the live cd. Deselect apic, lapic. If it boots then, you can continue and install from the live cd. The noapic,nolapic option will be automatically added to the kernel line in the grub menu. There are other possible causes but this is an easy way to test this one.

---

### Post by Ocke on 2009-06-09
> **ronparent said:**
> Have you tried it out by running the live cd? Does it load and run with no freeze? If no, then try hitting F6 - options at the first menu screen when booting the live cd. Deselect apic, lapic. If it boots then, you can continue and install from the live cd. The noapic,nolapic option will be automatically added to the kernel line in the grub menu. There are other possible causes but this is an easy way to test this one.

Thanks for your reply ronparent. 

The CD runs fine and I have tried deselecting and selecting all of them, but still the same result.

---

