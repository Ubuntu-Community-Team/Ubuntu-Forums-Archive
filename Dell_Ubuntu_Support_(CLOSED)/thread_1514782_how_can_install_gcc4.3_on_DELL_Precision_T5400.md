---
title: "how can install gcc4.3 on DELL Precision T5400"
date: 2010-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kwanu on 2010-06-21
Hello all,
 
I am using DELL Precision T5400 and Ubuntu10.04.
First time, I was trying to install Ubunut 9.04 and 9.10 on DELL precision T5400, but I could not do it. I do not know why.
 
So, I have installed the Ubuntu 10.04 on DELL precision T5400.
I need to use gcc4.3 not gcc4.4, because of compiling my own code. Actually, I am using c++ Boost library 1.36.0, but I think it is working with gcc4.3. 
As you know, there are gcc4.3 and gcc4.4 on Synaptic Package Manager in Ubuntu10.04, but if I select gcc, the Ubuntu10.04 select gcc4.4 automatically, even though I need gcc4.3.
 
So, do you guys know how can install gcc4.3 instead of gcc4.4?
 
Thanks,

---

### Post by kwanu on 2010-06-21
I have solved this.
 
sudo ln -s /usr/bin/gcc-4.3 /usr/bin/gcc
 
Thanks,

---

