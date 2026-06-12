---
title: "CPU usage mystery"
date: 2005-12-03
forum: Desktop Environments
---

### Post by meborc on 2005-12-03
hi

i read about mem usage just a few threads back and opened my system monitor just to take a look what is going on... and to my surprise i found out the following - the processes tab shows that under 30% of cpu is used by the system monitor itself... and thats it... but the resources tab shows that 100% of cpu is used... what is using it? i hoped it is a short term thing... but it just continued like this... and the interface seemed a bit slow and jerky... but it still kept on insisting that my cpu usage is 100% ... (and i believe that it is true as it was slow) but why is it not in the processes tab? any thoughts? or am i just mad? :D

---

### Post by Ampersand on 2005-12-03
If you open a terminal and run
```
top
```
Does it show any processes that seem to be using a lot of the processor?

---

### Post by meborc on 2005-12-04
if i open system monitor and use top in terminal, then 70% of cpu is used by xorg and rest used bu gnome sys monitor... it seems like xorg uses whatever is left from sys monitor... but when i close it, only 2% of cpu is used... so... wtf is up with xorg?

my comp specs:
AMD DURON 800Mhz, 250 RAM, GeForce 2 mx 200 (32MB), 40 GB HDD

---

### Post by meborc on 2005-12-05
bump... does anyone share my mystery? or am i alone?... the simple solution would be NOT TO USE the sys monitor... BUT :rolleyes: it would be nice to have it running properly

is this a bug to be reported, or have i messed my xorg up somehow? (i just made a reinstall of ubuntu breezy from official cd a few weeks ago... then apt-get update + upgrade... and i don't think i have made any major configuration on my system... so... it should be a bug... right?)

---

