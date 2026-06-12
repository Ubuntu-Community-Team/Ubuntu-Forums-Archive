---
title: "Nautilus crash when accessing trash under root"
date: 2008-06-10
forum: Desktop Environments
---

### Post by dupersuper on 2008-06-10
whenever i run nautilus using sudo, nautilus will hang when accessing the trash in the sidebar.
this didn't use to happen in the past. seems like a s/w update caused it.

the problem right now is that i have deleted some files in nautilus as root but as i am unable to empty the trash, i can't recover the space.

i noticed under the root home directory there is no .trash folder so i can't use rm to remove the files either.

does anyone know where does files deleted in root nautilus go? :(
thanks!

---

### Post by juanoleso on 2008-06-10
yeah, i had this same problem too.  I believe the trash goes to like /root/.local/share/Trash  something like that (sorry at work on a windows machine.)  I then rm'd the "files" folder in there and then recreated with the same permissions that it had before.

---

### Post by NilsE on 2008-06-10
There is a bug open in launchpad for this problem.  A suggested workaround until fixed is to launch nautilus with the following command

```
gksudo dbus-launch nautilus
```

---

### Post by dupersuper on 2008-06-11
> **NilsE said:**
> There is a bug open in launchpad for this problem.  A suggested workaround until fixed is to launch nautilus with the following command

```
gksudo dbus-launch nautilus
```

it worked! thanks. cleared up quite some space.

---

### Post by weremichael on 2008-08-14
> **NilsE said:**
> There is a bug open in launchpad for this problem.  A suggested workaround until fixed is to launch nautilus with the following command

```
gksudo dbus-launch nautilus
```

Sadly, this didn't work for me. I still get the follow error message: "Error removing file: Permission denied."

The files I want to delete only appear in the trash when I mount a second hard drive. The files were (and I guess still are) located on this second hard drive so I guess that makes sense. 

Anyone have a suggestion for permanently deleting these files??

---

### Post by billy_bob666 on 2008-09-09
Thanks i had the same problem
(gksudo dbus-launch nautilus) works :)
i recovered 56 gigs

---

### Post by AmberG on 2008-12-05
> **NilsE said:**
> There is a bug open in launchpad for this problem.  A suggested workaround until fixed is to launch nautilus with the following command

```
gksudo dbus-launch nautilus
```


So the bug is still open in 8.10 ?

I had this problem as well today - but this workaround WORKED for me.

Thanks

---

### Post by MollyWop on 2011-04-04
Worked for me in 10.10. : )

---

### Post by MarkVS on 2011-04-14
Worked for me as well :) You would think that they would have fixed it by now.

---

