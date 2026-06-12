---
title: "4 CPU's detected, only have 2"
date: 2009-05-05
forum: General Help
---

### Post by daser1220 on 2009-05-05
I just installed Ubuntu 9.04 on a dell workstation. The computer has two processors, each single core, but system monitor is detecting 4 CPU's. Can this be corrected?

---

### Post by wsonar on 2009-05-05
Can you do a print screen

are you sure it's not saying pentium 4 cpu

---

### Post by daser1220 on 2009-05-05
[http://img140.imageshack.us/my.php?image=21813380.jpg](http://img140.imageshack.us/my.php?image=21813380.jpg)

No, it's detecting 4 CPU's. In the resources tab it's showing four CPU's as well, each with different utilization percentages. BOINC is detecting this as well, and running more processes than it should and that is the only reason I have a problem with it.

Before you ask, I'm absolutely positive the two processors are single core, since it's a relatively outdated processor family. Until recently Windows Server 2003 was installed on this system, and this problem didn't exist, so it shouldn't be a BIOS problem either.

---

### Post by starcannon on 2009-05-05
Hyperthreading CPU's will sometimes show up as dual cores, if you have 2 of them, then it will look like 4 cores.

---

### Post by daser1220 on 2009-05-05
So can I fix  this without disabling hyperthreading in the bios?

---

### Post by wpshooter on 2009-05-05
> **starcannon said:**
> Hyperthreading CPU's will sometimes show up as dual cores, if you have 2 of them, then it will look like 4 cores.

Yes, I bet if you turn hyperthreading off in the BIOS, you will then only see 2 CPUs.

---

### Post by wpshooter on 2009-05-05
> **daser1220 said:**
> So can I fix  this without disabling hyperthreading in the bios?

My "guess" would be NO.

---

### Post by Brainy142 on 2009-05-05
Why would you want to "fix" it it is normal...

---

### Post by mikezila on 2009-05-05
There is no problem.  There's nothing to fix.  If you have two HT-enabled CPUs, then you have two cores, that can each run two threads at a time, hence 4 CPU graphs.

---

### Post by LoneWolfJack on 2009-05-05
you need to distinguish between physical and logical CPUs.

you have two processors (physical CPUs) but thanks to hyperthreading, linux can use them as four, so you have four logical CPUs showing. 

this can result in huge performance gains and is nothing that can/should/needs to be fixed.

---

### Post by 3rdalbum on 2009-05-05
Hyperthreading doesn't compromise single-thread performance.

You can read Wikipedia for the exact details of how it works, but this is my understanding:

Sometimes the CPU won't be able to execute an instruction until some data is fetched from memory, or until a previous instruction has passed completely through the pipeline. A non-hyperthreaded CPU will sit there and wait for the data to come through. A hyperthreaded CPU will execute instructions from another thread while it is waiting.

In Linux, there's often another thread or process to deal with. On Windows, hyperthreading can increase performance by up to 30% without penalty (situation dependent). On Linux you may see higher performance gains.

---

### Post by dcstar on 2009-05-05
> **daser1220 said:**
> 
No, it's detecting 4 CPU's. In the resources tab it's showing four CPU's as well, each with different utilization percentages. BOINC is detecting this as well, and running more processes than it should and that is the only reason I have a problem with it.
........

Then simply change your BOINC preferences - there is no "problem".

---

