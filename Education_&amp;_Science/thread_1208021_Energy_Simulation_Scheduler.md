---
title: "Energy Simulation Scheduler"
date: 2009-07-08
forum: Education &amp; Science
---

### Post by billstron on 2009-07-08
I've created a c based residential energy simulation that is run from the command line.  It takes inputs from a couple of command files and command line options.  It outputs data files to be read by matlab.  

I run the simulation on a dedicated multicore workstation because they take a long time.  Unfortunately, my problem is not parallizable.  (I've tried with no speed improvements.)  So in order to make better use of the multiple cores, I manually run multiple instances with different parameters in separate directories.  

I would like to automate the multiple jobs with some kind of job scheduler.  Ideally, I would be able to add other computers to the network and schedule jobs onto them from a single queue.  

Does anyone have a suggestion for how to accomplish this simply? So far, the thing that makes the most sense is Ruby Queue [http://raa.ruby-lang.org/project/rq/](http://raa.ruby-lang.org/project/rq/), but I cant find very much documentation.  

Thanks!
Bill

---

### Post by billstron on 2009-07-09
Bump!  No one has tried this?

---

### Post by InfernalNeutrino on 2009-07-09
The lab I work at uses torque [(clicky)]("http://www.clusterresources.com/products/torque-resource-manager.php") to handle their batch jobs across multiple computers. I don't know if it is overkill for your purposes simply because my experience with it is entirely as an end-user - i.e. submitting jobs and waiting for the results :) . I don't use ubuntu any more, but IIRC there is a package with it somewhere in the repository. I also believe there are some howto's floating around the internet, but I never really looked at them because, again, I never actually had to set it up myself. Good luck!

---

### Post by samrick06 on 2009-07-12
Hai...
 
I m the new memeber of this group & i found many impressive comments given by others,it's really promoting.
 
[technorati]("http:\\www.technorati.com")
 
==========================
samrick

---

