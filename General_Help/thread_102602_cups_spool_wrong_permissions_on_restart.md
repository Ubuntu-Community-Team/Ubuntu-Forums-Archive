---
title: "cups spool wrong permissions on restart?"
date: 2005-12-12
forum: General Help
---

### Post by billw@onedrous.org on 2005-12-12
Hi,

I've got an Epson Stylus Color 640 attached to a parallel port on my linux box. I can reliably print from linux, but I can only print from a windows machine via samba if I manually change the permissions of the cups spool to 1777:

 chmod -R a+rwxt /var/spool/cups

If cups is restarted, the permissions of the spool revert back to 1770.

I've tried changing the RunAsUser parameter of cupsd.conf to No, but that had no effect. For now, I've hacked /etc/init.d/cupsys to execute the chmod command after starting the daemon, but that seems like a bad idea. In fact, I'm not even certain that the spool's permissions should be expanded in that manner.

Does anyone on this forum have any advice on this matter?

Thanks,

 -Bill

---

