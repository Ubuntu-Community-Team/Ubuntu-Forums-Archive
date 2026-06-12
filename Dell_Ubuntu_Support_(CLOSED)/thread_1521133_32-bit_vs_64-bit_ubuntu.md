---
title: "32-bit vs 64-bit ubuntu"
date: 2010-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by n4pgw on 2010-06-30
I just discovered that my desktop computer, Dell Diminsion 3000 is 32 bit, which is no surprise, but my Dell laptops are both 64-bit.  One is an Inspiron 1501 and the other is an Inspiron 1545.

I have installed on all three Ubuntu 10.04.  However, I did not select 64 bit so I assume they are all running 32 bit Ubuntu.  

How do I know if the OS is 32 or 64 bit?

Should I upgrade the laptops?

If so, how do I upgrade them?

Thanks
Buck

---

### Post by squaregoldfish on 2010-06-30
uname -m will tell you whether you're running 32-bit (i686) or 64-bit (x86_64).

As for whether to switch to 64-bit, there's endless discussions on the subject in the forums. In short though, it won't do any harm, and might do some good - depending on what you're doing with your machines.

Steve.

---

### Post by n4pgw on 2010-06-30
Thanks, Steve,

As suspected, I am running 32 bit.  I'll search the forums to see which is better.

Buck

---

### Post by recluce on 2010-07-08
Bascially, it comes down to the amount of RAM in your machines. Less than 4 GB, no difference between the two versions. 4 GB or more: 32bit will not allow you to use all your RAM.

---

### Post by bobcollard on 2010-07-08
Actually it depends on which Kernel you are using.  A 32 bit system with 2.6.32-23-generic PAE will utilize 4GB of RAM.  So it depends on the distribution.  Linux Mint uses PAE on their 32 bit systems and it is based on Ubuntu.  I am using Xubuntu 10.04 x86_64 and it is fast on my 1545.  I have 4GB RAM, the max for this computer.

---

### Post by n4pgw on 2011-03-21
Thank you all for your replies.  I don't have 4GB RAM in any machine, so I will stick to 32.  However, my new computer is planned to have 6-8 GB RAM so I will try it there.

---

