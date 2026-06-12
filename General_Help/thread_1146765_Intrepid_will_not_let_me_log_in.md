---
title: "Intrepid will not let me log in"
date: 2009-05-02
forum: General Help
---

### Post by lars25700 on 2009-05-02
Hard facts: 
System: intel based dual core (fujitsu siemens MB), 3GB RAM
Graphics: Nvidia 9600

I was watching a DVD (like many times before using VLC). 

after no apparent reason the system is not letting me log in after a reboot. 

I wanted to install a package which required me to login as su. Trying to do so gave me an error "segmentation fail" 

I thought: "some bug" and rebooted.

After having done so I am not able to log in the graphical login anymore. 

Tried terminal via CTRL+ALT+F1 - brings the terminal login but when I enter my user and pass it doesn't let me let me login either. 

Would be great if anyone had an idea. If you need more info please let me know which and how I can obtain it. 

Thanks

---

### Post by Eisenwinter on 2009-05-02
Hm.

Try the fallback kernel. Boot into that, if you are thrown into a terminal, log in, and type startx.

Report results.

---

### Post by lars25700 on 2009-05-02
> **Eisenwinter said:**
> Hm.

Try the fallback kernel. Boot into that, if you are thrown into a terminal, log in, and type startx.

Report results.

Thanks for the fast reply - same bitchy results though... 

Is my Ubuntu a woman?

---

### Post by lars25700 on 2009-05-02
Updated info: 

while in non-graphical mode it speaks: 

kinit: name_to_dev_t(/dev/disk jada jada jada)
kinit: trying to resume from /dev/disk/ jada jada jada
kinit: No resume image, doing normal boot... 

any help?

---

### Post by lars25700 on 2009-05-03
Anyone?

---

