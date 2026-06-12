---
title: "Compile or not compile"
date: 2008-12-27
forum: General Help
---

### Post by Alexbit on 2008-12-27
Hi all,
From some months I'm using *only* ubuntu on my laptop.
I've an Acer Aspire 1513LMi that comes with an Athlon 64 3400+, geForce FX go5700 (64Mb), 512 Mb of Ram (DDR), and a 120 GB of storage (5400 rpm).
Ubuntu 8.04 (with latest patch) works fine but it's quite slow during boot-up and sometime during usage.
I've just follow the instruction at: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) and [http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

I want to ask you if I recompile kernel i can get better performance.

"Obviously", if is it, i'm not just skilled to do that but in that case I can read.... :P

Thank you all,
Ale

---

### Post by SonnHalter on 2008-12-27
why not just upgrade to intrepid?

---

### Post by Alexbit on 2008-12-27
> **SonnHalter said:**
> why not just upgrade to intrepid?

I don't think that this solve my question.
I'm looking for a way to optimize performance of my current distro.
I also think that 8.10 (intrepid) is newer than 8.04 (hardy) but that not means a priori that it's more fast or optimized for my hardware.

---

### Post by jespdj on 2008-12-27
Compiling your own kernel will most likely not make your system boot much faster.

---

### Post by sdennie on 2008-12-27
I agree with jespdj.  Compiling your own kernel isn't going to help in your case.  Upgrading to 1G of RAM or more will likely take care of any speed problems you have during runtime.  Boot times are what they are.  A faster disk will help but, in general, there isn't much that can be done to make it drastically faster unless you are willing to spend a huge amount of time trying to solve the problem.  Apparently Jaunty is going to address boot times but, on a laptop, I *highly* recommend you use suspend/resume.  Then your "boot time" is about 5 seconds, all your apps are already open and the disk cache is already populated.

---

### Post by Alexbit on 2009-01-02
> **vor said:**
> I agree with jespdj.  Compiling your own kernel isn't going to help in your case.  Upgrading to 1G of RAM or more will likely take care of any speed problems you have during runtime.  Boot times are what they are.  A faster disk will help but, in general, there isn't much that can be done to make it drastically faster unless you are willing to spend a huge amount of time trying to solve the problem.  Apparently Jaunty is going to address boot times but, on a laptop, I *highly* recommend you use suspend/resume.  Then your "boot time" is about 5 seconds, all your apps are already open and the disk cache is already populated.

During the past few day I've plan and done the migration from hardy to intrepid.
Now all seems to work fine.
Performace are similar but I found in intrepid many change that I like.
Till now I think to remain with intrepid.
I'm considering the idea to upgrade the amount of ram but it costs much for my "old" machine.
If a found some more money I buy it for sure.
Suspend function (both in hardy and intrepid) freeze my machine on resume so I can't use.
At the end I've understand that compiling is not for me (now) :)

If is it possibile, can you say some usefull guide to optimize intrepid?

Thank you all for the right information!
Have a nice day!
Alessio

---

### Post by zvacet on 2009-01-02
You can read [this]("http://ubuntuforums.org/showthread.php?t=89491&highlight=optimize+ubuntu") and see if it is of any help to you.

---

