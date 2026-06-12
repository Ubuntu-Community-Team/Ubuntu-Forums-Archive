---
title: "Power failure during update - can't boot updated kernel"
date: 2009-06-23
forum: General Help
---

### Post by prunesquallor on 2009-06-23
A few updates arrived, including kernel 2.6.28-13, which were being installed. Unfortunately the mains power failed during the process and I can't boot from the using the new kernel (2.6.28.13). I can boot OK from the older kernel in grub so it isn't much of a problem.

However, is it possible to reinstall/reconfigure the update the was being installed when the mains power failed?

Thanks.

---

### Post by Closed_Port on 2009-06-23
Did you try sudo apt-get -f install?

This should fix packages that weren't installed properly.

---

### Post by prunesquallor on 2009-06-23
Thanks for your reply. 

I tried sudo apt-get -f install which led to a message informing me O should do sudo dpkg --configure -a. This I duly did with the result of some packages being configured. But, the new kernel update still produces a kernel panic.

It isn't any big deal, I'll simply use the older kernel.

---

