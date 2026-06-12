---
title: "constant crashes"
date: 2006-01-17
forum: Desktop Environments
---

### Post by bonbon64 on 2006-01-17
just installed ubuntu 5.10 -- 2.6.12-10-386 not to long ago everything went fine exept it keeps hard locking all that moves is the curser

 i have installed the latist nvidia drivers NVIDIA-Linux-x86-1.0-8178-pkg1, turned of power management, i even did a clean install to see if i could stop it happening didnt work 

i am not sure if i should mess around with the xorg.conf file becuase i read that it was edited automatically by the driver.
-- and for the first time ever only the bottom bar has frozin as i am writing this
i have been strugling with this for about 3 solid days, i have attached my xorg.conf and log files to see if you can see anything

ben

athlon xp amd 2400+, gigabyte k7 mobo, gforce 6600 128mb,

---

### Post by bonbon64 on 2006-01-17
oh well i keep looking on the post see if i cant find a soltion, think i will stick to ubuntu for just now (no more reformating):???:

---

### Post by bonbon64 on 2006-01-17
i got it working if any is itersted, say that it will problly crash in minute - i added   	Option         "NoRenderAccel" to deivie in the xorg.conf file

---

