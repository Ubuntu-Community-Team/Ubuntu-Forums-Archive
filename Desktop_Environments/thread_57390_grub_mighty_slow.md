---
title: "grub mighty slow"
date: 2005-08-16
forum: Desktop Environments
---

### Post by synaptic revolt on 2005-08-16
Grub adds about 30-45 seconds to my boot time. Any way to speed this up? I should note that it's only my main desktop that has this problem. The laptop and second desktop boot fast :)

---

### Post by recce101 on 2005-08-16
[QUOTE=synaptic revolt]Grub adds about 30-45 seconds to my boot time. Any way to speed this up? I should note that it's only my main desktop that has this problem. The laptop and second desktop boot fast :)[/QUOTE]
What's the timeout value in /boot/grub/menu.lst? I've set mine to 5 seconds versus the default 10. Maybe yours accidentally got set to something more than 10....?

---

### Post by synaptic revolt on 2005-08-16
[QUOTE=recce101]What's the timeout value in /boot/grub/menu.lst? I've set mine to 5 seconds versus the default 10. Maybe yours accidentally got set to something more than 10....?[/QUOTE]

It's set at 10, but the problem is that it takes forever for the grub menu to show up.

---

### Post by synaptic revolt on 2005-08-17
halp!

---

### Post by Muhammad on 2005-09-05
ME TOO!

I think something is wrong with my BIOS driver/update or sumthin

mine is Intel D865GBF.

---

### Post by pirast on 2005-10-23
If you still have this problem please help solving it:

[https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245](https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245)

---

