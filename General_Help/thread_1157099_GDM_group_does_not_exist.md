---
title: "GDM group does not exist"
date: 2009-05-12
forum: General Help
---

### Post by kyotol on 2009-05-12
I'm a newbie and really trying to learn more, but this one has my really confuesed. Searching is turning up hardly anything useful. Today I turned on my computer and saw this: 

chown: invalid group: ' syslog:adm' 

then it was repeated about sixteen times down my screen and was followed by this: 

chown: invalid group: 'klog:klog' 

That was repeated twice. After about a five to ten minute wait, the system would finally continue on and this message would pop-up:

The GDM group 'gdm' does not exist. Please correct the GDM configuration and restart GDM.

I hit ok, and it would give me a login prompt. I logged in and typed:

sudo dpkg-reconfigure gdm

I get the error: Sorry user (my username) is not allowed to execute '/usr/sbin/dpkg-reconfigure gdm' as root on (my computer name)

So, I really need help. The only things that have changed on the computer was the upgrade to 9.04 which went smoothly and I added a new user.

---

