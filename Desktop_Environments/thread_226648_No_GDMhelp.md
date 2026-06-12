---
title: "No GDM:help"
date: 2006-07-31
forum: Desktop Environments
---

### Post by chintan_agarwal on 2006-07-31
A funny thing happened when I booted my comp today morning, there's no display. There's an error saying "can't find /usr/share/gdm/.../HumanCircles.xml". So I rebooted in safe mode. Lo and behold, what I find is that there is someting /usr/share/gdm but it has some funny mode(I did ls -la). The mode is something like ?rwSrwsrw- (I guess it should look like drwxrwxrw-). Now I am not able to do anything(as there's no display. Can somebody please tell me how to correct this problem, or at least go about it.
Thanks.
-Chintan

---

### Post by Ziox on 2006-07-31
try purging GDM and then reinstalling it...

sudo aptitude purge gdm

sudo aptitude install gdm

maybe you don't even have to purge gdm...maybe a reinstall of gdm will do...

sudo aptitude reinstall gdm

---

### Post by chintan_agarwal on 2006-08-01
> **Ziox said:**
> try purging GDM and then reinstalling it...

sudo aptitude purge gdm

sudo aptitude install gdm

maybe you don't even have to purge gdm...maybe a reinstall of gdm will do...

sudo aptitude reinstall gdm

No luck. Purging fails for gdm(and install has no effect). In fact I tried to remove(rm gdm) the gdm directory manually as a su, but it says that cannot delete "wierd file" gdm. I am also not able to rename the directory(If I am able to, I might replace the gdm directory with the correct one!). Any other suggestions and any idea why this happened?

---

