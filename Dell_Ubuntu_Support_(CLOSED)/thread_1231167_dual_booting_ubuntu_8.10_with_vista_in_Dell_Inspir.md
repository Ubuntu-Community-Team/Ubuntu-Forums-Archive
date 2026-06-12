---
title: "dual booting ubuntu 8.10 with vista in Dell Inspiron 1525"
date: 2009-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dinesh_ddt on 2009-08-04
Hi guys,

Im want to dual boot my vista with ubuntu 8.10 on my dell inspiron 1525..
i have 5 drives c(vista), d(recovery), e,f and a I drive..
i want to install ubuntu in I drive(15gb capacity)

Im unable to install with the live CD..

plz help me out..

also some ppl told me abt swap swap swap..:confused::confused:
wat is it? should i allot some space for it??

---

### Post by realzippy on 2009-08-04
You could boot your 8.1 as LiveCD with internet access,then install
gparted.
Open a terminal and type :

sudo apt-get install gparted

when its done,type:

gparted

A GUI will open,delete your "I" partition so it will become free disc space.
Start Installation,when it comes to partion choose:
"use free space" or sort of that...

---

### Post by joriad on 2009-08-04
To run Gparted from Intrepid Ibex all yoou need to do is run the live cd then open terminal and type Gparted. you do not need internet nor do you need to download Gparted. Gparted comes packaged in 8.10.

---

### Post by realzippy on 2009-08-04
> **joriad said:**
> To run Gparted from Intrepid Ibex all yoou need to do is run the live cd then open terminal and type Gparted. you do not need internet nor do you need to download Gparted. Gparted comes packaged in 8.10.

...was not shure about it.But type "gparted",not "Gparted"

---

### Post by joriad on 2009-08-04
> **realzippy said:**
> ...was not shure about it.But type "gparted",not "Gparted"

Yep, Just use to capitalising proper names. So sometimes I forget to enter lowercase when it comes to Linux.

---

### Post by dinesh_ddt on 2009-08-04
Thanks a lot..
and can i install ubuntu in logical partition ?

---

### Post by realzippy on 2009-08-04
yes

---

