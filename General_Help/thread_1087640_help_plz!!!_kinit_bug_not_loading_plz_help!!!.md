---
title: "help plz!!! kinit bug not loading plz help!!!"
date: 2009-03-05
forum: General Help
---

### Post by meinvateristnein on 2009-03-05
ok get an error looking like this trying to resume from /dev/disk/uuid .............. i forget the rest but it doesnt load and says resume image not found  ........ im pretty sure this is a bug

this bug seems to happen alot on acer machines and i know 6 people with this exact problem..... this happened after installing ati drivers..... on the 20th boot up

---

### Post by Chandler258 on 2009-03-05
I had simillar problems with Nvidia. Did you use Envy, did you download and install them yourself or did Ubuntu suggest proprietary drivers for you?

---

### Post by meinvateristnein on 2009-03-05
installed myself

---

### Post by luapekralc on 2009-03-05
Hi,

I had the same problem after I installed (probably incorrectly) a new version of Python.

I found this on how to reinstall the Ubuntu desktop from the command line. 

 $ sudo tasksel install standard
 $ sudo tasksel install ubuntu-desktop

I haven't tried it yet, but it looks promising.

---

### Post by abn91c on 2009-03-05
> **meinvateristnein said:**
> ok get an error looking like this trying to resume from /dev/disk/uuid .............. i forget the rest but it doesnt load and says resume image not found  ........ im pretty sure this is a bug

this bug seems to happen alot on acer machines and i know 6 people with this exact problem..... this happened after installing ati drivers..... on the 20th boot up
at the login in prompt enter your user name and password then **startx**
if you get the same error with a **initramfs prompt** type **exit**

---

### Post by luapekralc on 2009-03-06
> **luapekralc said:**
> Hi,

I had the same problem after I installed (probably incorrectly) a new version of Python.

I found this on how to reinstall the Ubuntu desktop from the command line. 

 $ sudo tasksel install standard
 $ sudo tasksel install ubuntu-desktop

I haven't tried it yet, but it looks promising.

This worked well - Ubuntu Desktop is now working fine

---

