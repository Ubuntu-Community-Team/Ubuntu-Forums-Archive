---
title: "Manual Partitioning While Installing Intrepid Ibex 8.10"
date: 2009-01-27
forum: Desktop Environments
---

### Post by sharathpaps on 2009-01-27
Hello,
       I'm relatively new to Ubuntu & I now want to install Ubuntu as the only OS on my laptop. I have an 80GB HDD with 1.5GB RAM. I'm assuming an 80GB HDD will have ~75GB of usable space. This is how I plan to partition the HDD. Please check if what I plan to do is O.K and correct me if I've got it wrong. So,

Root Partition -> Size: 10GB, Mount Point: / **or should it be /boot?** 

Home Partition -> Size: 62GB, Mount Point: /home

Swap           -> Size: 3GB,  Mount Point: **What goes here?**

Will the above setup allow me to reinstall Ubuntu when required without affecting my /home partition? Since I'm still learning, I expect that I'll mess my system up at some point or the other :p

Thanks in advance. I know people have asked similar questions elsewhere, but the solutions there didn't cut it which is why I seek to clarify.

---

### Post by markusf21 on 2009-01-27
that sounds about right. 
root gets mouted to /
swap is mounted as swap (its in the scroll down list)

---

### Post by adamlau on 2009-01-27
Unless you are running server, or intend to compile for 64 GB memory support, swap = 2.5 GB.

---

### Post by sharathpaps on 2009-01-27
Thanks guys...I'll do that then...

---

### Post by agarzon on 2009-02-25
is your /home partition primary or logical?

---

