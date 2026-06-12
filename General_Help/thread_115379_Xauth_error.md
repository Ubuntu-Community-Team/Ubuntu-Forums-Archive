---
title: "Xauth error"
date: 2006-01-10
forum: General Help
---

### Post by steved27 on 2006-01-10
Hi, 

I rebooted the other day and now Xorg won't start. When I type startx (or try to start through gdm) i get the following fatal error from the X server:

Could not copy /var/log/Xorg.0.log  to Xorg.0.log.old

If I try to copy the file manually using sudo, I get that Xorg.0.log.old is write protected, not sure if it's supposed to be or not.  

If I try again I get a number of errors relating to xauth not being able to create files in my home directory and then the same error. 

I've tried running 

dpkg-reconfigure xserver-xorg 

with no luck.  

I've also tried running 

dpkg-reconfigure xauth 

with no result either.  

Wish I could remember everything I'd done before the reboot, but I'm not sure at this point everything that I had installed/upgraded/changed. 

Anyone have any ideas?  

Thanks

---

