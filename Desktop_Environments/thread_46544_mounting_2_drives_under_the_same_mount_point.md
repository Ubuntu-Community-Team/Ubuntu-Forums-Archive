---
title: "mounting 2 drives under the same mount point"
date: 2005-07-05
forum: Desktop Environments
---

### Post by kubuntuuser on 2005-07-05
Does anyone know if it is possible to mount 2 physical drives under 1 mount point.

I have a laptop with the following config

30 gig total
------------------
ntfs - 23gig windows
ext3 - 4gig /
ext3 - 2gig /home
swp - 1gig /swap

I am fast running out of space but really dont want to re partition and then reinstall.

I would like to create a new partition from free space on my windows partition and have it mounted with the current "/" partition to give / more space.

I performed a default install originally and use kubuntu.

Many thanks

---

### Post by Juergen on 2005-07-05
AFAIK only if you had used LVM or something like that from the beginning.

Maybe you could try [http://www.unionfs.org](http://www.unionfs.org)

---

### Post by uberlinux on 2005-07-05
I like to just mount storage drives under something new like /storage or /archives  I have gone through a ton of formats and been able to keep the same drives, and doing that with dual boot between ubuntu/flavor of the week I have been able to mount it the same under all the OS's I switch between.

---

### Post by kubuntuuser on 2005-07-05
I want to increase my / partition so i can install apps via apt-get and synaptic so that wont really work for me. 

Thanks though, keep suggestions coming?

Is there any way to get LVM up and running after an install?

---

