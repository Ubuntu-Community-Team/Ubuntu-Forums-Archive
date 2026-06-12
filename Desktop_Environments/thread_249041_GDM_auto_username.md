---
title: "GDM auto username"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Illusionistx on 2006-09-02
I'm not looking for an automatic login solution. 
what i do want is for the gdm to either automatically fill in a specified username, or just use the specified username and only have to enter the password. is this possible?

---

### Post by aysiu on 2006-09-02
I don't think GDM can do this, but you can always do this in KDM (and still use Gnome--yes).

---

### Post by Illusionistx on 2006-09-02
ok, so i installed kdm and when i reboot it always freezes at Loading Hardware Driver... so i just tried to boot into recovery mode, and i get this
```
<0>Kernel panic - not syncing: Fatal exception in interrupt
```
is there anything i can do about this??

---

### Post by mindtrick on 2006-09-02
how can we switch between kdm and gdm?

---

### Post by Illusionistx on 2006-09-02
when installing kdm it gives the option to choose which you want as default. and if it doesn't then edit /etc/init.d/gdm and kdm
anyways, back to my question: is there anyway i can fix this panic?

---

### Post by Illusionistx on 2006-09-02
anyone? i can't boot at all. if i were to be able to boot from a live cd, whihc i haven't tried yet, could i change anything or fix anything?

---

### Post by Illusionistx on 2006-09-02
fixed it. my averatec 3500C has a bios option to set the size of shared memory, video and RAM. i just increased it and it worked.

---

### Post by sdebo on 2006-09-02
good for you, but cryptic system feedback there.
How did you realise you had to modify the BIOS?

---

### Post by Illusionistx on 2006-09-02
just a guess. everything worked before i had set to use KDM by default. i knew i had very little shared video ram, so i thought that it might've been the cause for some reason. i really didn't have an exact reason i just tried it and it worked.

---

