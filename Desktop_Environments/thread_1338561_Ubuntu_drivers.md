---
title: "Ubuntu drivers"
date: 2009-11-26
forum: Desktop Environments
---

### Post by BALJEET OBEROI on 2009-11-26
Hi everybody 
i have installed ubuntu on my  hcl laptop which was initially having windows xp 
i have completely formatted & installed ubuntu 9.10
where can i find drivers for my hcl laptop 
i.e 
wifi driver
graphic card driver

---

### Post by scorp123 on 2009-11-26
Let go of your Windows-thinking. All kernel modules (= "drivers") are already there where they belong: In the kernel.

There is no "go to website xyz and hunt for driver xyz" here.

The downside is that if your hardware is not supported "out of the box" it can become difficult to get it working.

So to get you started ... tell us more about your laptop and its hardware. If something is not working then the people on this forum can help you ...

---

### Post by BALJEET OBEROI on 2009-11-27
My laptop config are as follows 
160gb hdd
1gb ram 
intel dual core processor 
i am not able to configure & use wifi on my ubuntu loaded laptop
how can i configure wifi on my ubuntu laptop

---

### Post by andrea000 on 2009-11-27
Hi again

what your looking for i think is proprietary drivers
go to system->administration->hardware drivers and look
there if there is any activate them.

---

### Post by BALJEET OBEROI on 2009-11-27
Thanks for your suggestion 
 
but i am not able t configure wifi on my laptop 
how can i view that my wifi drivers are installed or else hw can i use wifi 
 
on windows when i enable my wifi it asks automatically for drivers but its not the same case over here 
 
how shll i proceede

---

### Post by Grenage on 2009-11-27
Plug your laptop in using the network port; assuming you can then access the network:

sudo apt-get update (in a terminal)
sudo apt-get upgrade

Then go to System/Administration/Hardware drivers and check for wireless drivers being available.  I had the same issue, no drivers listed until after an update.

---

