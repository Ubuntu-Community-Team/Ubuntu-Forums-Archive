---
title: "[SOLVED] ubuntu not booting"
date: 2008-12-08
forum: General Help
---

### Post by abhilashm86 on 2008-12-08
my ubuntu 8.04 version is not booting,when the GRUB loader shows up,i select ubuntu after that this message comes
loading 
please wait
after a minute also my ubuntu is not booting,please help

---

### Post by eBoxNet on 2008-12-08
did you try recovery mode?

---

### Post by abhilashm86 on 2008-12-08
yes i tried,thats also not working,should we give somr commands there

---

### Post by eBoxNet on 2008-12-08
are you getting any error message or its just don't boot?

---

### Post by abhilashm86 on 2008-12-08
> **eBoxNet said:**
> are you getting any error message or its just don't boot?

No messages or errors are displaying,just it asks loading please wait
thats all,can i use command mode and recover

---

### Post by eBoxNet on 2008-12-08
did you upgrade something or anything like that ?

---

### Post by abhilashm86 on 2008-12-08
> **eBoxNet said:**
> did you upgrade something or anything like that ?

no i din't upgrade to new version,yesterday i did boot splash images,maybe thats the problem......is there any method to recover

---

### Post by eBoxNet on 2008-12-08
any luck with older kernels?

---

### Post by abhilashm86 on 2008-12-08
> **eBoxNet said:**
> any luck with older kernels?
yup i tried the recover mode with old kernels,it din't boot at all,so what are the options with me now????

---

### Post by eBoxNet on 2008-12-08
are u sure ubuntu don't boot or you just can't c graphics
do you hear any sound ? is your hdd working?

---

### Post by abhilashm86 on 2008-12-08
when i use recover method,these messages are displayed
sd 0:0:0:0[sda] write proctect is off

sd :<4>driver 'sr' needs updating-please use bus_type methods

---

### Post by abhilashm86 on 2008-12-08
> **eBoxNet said:**
> are u sure ubuntu don't boot or you just can't c graphics
do you hear any sound ? is your hdd working?

yes eboxnet,my hdd is fine,no i don't hear any sound because ubunutu doesn't load,now currently i am replying from windows xp which is partitioned using GRUB..........

---

### Post by pietjanjaap on 2008-12-08
> **abhilashm86 said:**
> no i din't upgrade to new version,yesterday i did boot splash images,maybe thats the problem......is there any method to recover

Is this inside of grub, the splash image, then download supergrub, and then boot from supergrub and install it.

---

### Post by abhilashm86 on 2008-12-08
> **pietjanjaap said:**
> Is this inside of grub, the splash image, then download supergrub, and then boot from supergrub and install it.

can u please tell the procedure of doing it,should i perform these in command line of GRUB?

---

### Post by abhilashm86 on 2008-12-08
> **abhilashm86 said:**
> can u please tell the procedure of doing it,should i perform these in command line of GRUB?

friends i downloaded grub menu.lst from internet and repaired thr GRUB menu.lst. So it was my mistake yesterday coz i had edited menu.lst for boot splash images,i ran ubuntu in older kernels there some command options came and i had option of repairing boot options, thanks GOD at the end i successfully repaired,i would have posted error but it was in command mode...........

---

