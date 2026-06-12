---
title: "Kernel problem with updates"
date: 2009-05-07
forum: General Help
---

### Post by sports fan Matt on 2009-05-07
When I tried to update..I got this : inux-restricted-modules-generic:
 Depends: linux-restricted-modules-2.6.28-12-generic  but it is not installable


Is it a broken package or what?  Can I remove it?

---

### Post by Prominence on 2009-05-07
Same, I'm really hoping for a fix on this soon...I have no wireless because of this and I'm relying on a router I plug into my computer to get it...and it's horrible

---

### Post by sports fan Matt on 2009-05-07
this looks like a very old kernel..but im not sure

---

### Post by buntunub on 2009-05-07
Considering Jaunty is running the 2.6.28-11-generic kernel, I should think that the -12 kernel is somewhat in the future.

---

### Post by SciFi-Bob on 2009-05-07
Check you /etc/apt/sources.list, and see if you have any entries there that may install any custom kernels.

If that's not true, then I would guess that you (or some software package you manually installed) accidentially happened to compile and install a custom kernel at some time

In that case, you need to do a "dpkg -l|grep linux-image" find out what kernel you really are running.

---

### Post by fooman on 2009-05-07
i believe that is the latest kernel from the "jaunty-proposed" repository.

....so if you *un*check that repo in system > administration > software sources > updates

you should not see that warning anymore.

i saw that warning yesterday and since i do not use any restricted drivers (i install my nvidia drivers manually),  i figured it would be safe to uninstall the "linux-restricted-modules".  mine also came with a warning about "linux-generic".   so,  first i crossed my fingers for luck...then i went ahead,  uninstalled both of them and rebooted.

i am still here and have seen no ill effects.

now i am not recommending that anyone else uninstall those as they may very well be needed....but i have done so and everything seems to be working fine.  :)

---

### Post by kulight on 2009-05-07
this is related to the proposed repos' which having a bug...

[https://bugs.launchpad.net/bugs/372876](https://bugs.launchpad.net/bugs/372876)

---

### Post by sports fan Matt on 2009-05-07
that worked brilliantly...

---

