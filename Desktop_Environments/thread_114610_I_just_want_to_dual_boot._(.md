---
title: "I just want to dual boot. :("
date: 2006-01-08
forum: Desktop Environments
---

### Post by Leiki on 2006-01-08
I know there are a lot of threads on this, but nothing seems to help. I did the thing that someone posted on the "Dual booting for noobies" and that didn't seem to work. It can't be that hard, right? So how in the world can I dual boot Ubuntu and Windows?

P.S. - This is for my laptop. My computer is pure linux, baby.

---

### Post by aysiu on 2006-01-08
Was the "dual booting for newbies" the fifth link of my signature?

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=Leiki]I know there are a lot of threads on this, but nothing seems to help. I did the thing that someone posted on the "Dual booting for noobies" and that didn't seem to work. It can't be that hard, right? So how in the world can I dual boot Ubuntu and Windows?

P.S. - This is for my laptop. My computer is pure linux, baby.[/QUOTE]
You should install Windows, and if it gives you the option to not use the entire hard disk, don't use it.  Otherwise, after you install, use GParted to shrink the Windows partition(s).  Then when installing Ubuntu, choose the unformatted partitions to install on.  Pretty simple.

---

### Post by crispy_420 on 2006-01-09
Install Windows. If you have the option to setup partition size, leave what you want to use Ubuntu to use as blank(no format makes it easier to find). If you have an OEM Windows it might just format the whole disc. In that case you will need a Windows program like Partion Magic ([http://www.symantecstore.com/dr/sat1/ec_MAIN.Entry17c?CID=189671&PN=5&SP=10007&SID=49997&PID=705807&API1=65&API2=GOOGLE&API3=partition_magic_exa&API4=Google&API5=www.google.com&CUR=840&DSP=&PGRP=0&ABCODE=&CACHE_ID=189671]("http://www.symantecstore.com/dr/sat1/ec_MAIN.Entry17c?CID=189671&PN=5&SP=10007&SID=49997&PID=705807&API1=65&API2=GOOGLE&API3=partition_magic_exa&API4=Google&API5=www.google.com&CUR=840&DSP=&PGRP=0&ABCODE=&CACHE_ID=189671"))
Or something like it. Just resize Windows partition for what you need for Ubuntu. Then reboot to create the partition.

Now you can install Ubuntu and during the install you should see the free space.

That is what I did on my laptop anyway. Just a thought. I did it after a fresh install of WinXP Home so that if I screwed, it was no loss.

Good luck!

---

