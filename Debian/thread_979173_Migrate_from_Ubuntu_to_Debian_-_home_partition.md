---
title: "Migrate from Ubuntu to Debian - home partition"
date: 2008-11-11
forum: Debian
---

### Post by tuberculo on 2008-11-11
Hi, I use Ubuntu, but I have installed Debian in another partition and now I want to use it as my main OS. I have Ubuntu "/home" folder in a separate partition. How can I keep all the configurations of the applications? Is it safe to edit fstab in Debian to mount the home partition?

---

### Post by dptxp on 2008-11-14
you can not use the /home for Ubuntu for Debian.

---

### Post by snowpine on 2008-11-14
Actually I believe it is safe to use the same /home for both Debian and Ubuntu provided you use different usernames so the configuration files are stored separately.

---

### Post by p_quarles on 2008-11-15
> **dptxp said:**
> you can not use the /home for Ubuntu for Debian.
It *might* lead to problems, but I see no basis for stating that it certainly won't work. 

Especially since I've ported home directories between the two several times.

---

### Post by markharding557 on 2008-11-15
> **snowpine said:**
> Actually I believe it is safe to use the same /home for both Debian and Ubuntu provided you use different usernames so the configuration files are stored separately.

This is correct,you must use a different user name for each you will have two separate folders in the home directory

---

### Post by maybeway36 on 2008-11-16
As long as you're not using both OSes at the same time, it should be OK to use the same username. You will probably have to change your GNOME theme, though.

---

### Post by markharding557 on 2008-11-16
> **maybeway36 said:**
> As long as you're not using both OSes at the same time, it should be OK to use the same username. You will probably have to change your GNOME theme, though.

If you use the same user name when using the same home partition for two o/s the first will get corrupted by the second so the solution is to use a different user name so everything will be in its own folder.
this is what i do,i have debian sid and ubuntu

---

