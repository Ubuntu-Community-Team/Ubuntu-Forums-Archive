---
title: "Issue running DOS programs in DOSBox"
date: 2009-02-16
forum: General Help
---

### Post by RVA Dennis on 2009-02-16
While I can run the program I wrote in QB45 in 8.10, I can not access the data files which generate information to use in my currency trading work. I attempted to copy in to my user file but nothing the program can not find the database files. 

In WinXP, where I had run these programs previously they were located in "c:\forex\...." or whatever similar title. 

Is there anyone who can help me sort out how to link the program to the database files so that I can run these programs? 

Between wine and dosbox I can solve all of my migration to Ubuntu problems but it is absolutely necessary to be able to pursue my trading. 

NB. Since I am 67 and have been writing these programs in DOS based versions of Basic and QB45 since the days of my Radio Shack Model 100 "laptop" I haven't the time or patience to learn another language such as Python or C or ....

Thanks all!

---

### Post by Zalbor on 2009-02-16
I'm not sure if I understood 100% what your problem is, but in order for a program in DOSbox to see some files, these files have to be in DOSbox's "virtual" drive. For example, if you have mounted your ~/.dosbox directory as C:, the "forex" directory has to be in ~/.dosbox/forex .

---

### Post by RVA Dennis on 2009-02-16
I think I get the idea, now I'll see if I can do that.

Thanks Zalbor, I'll give it a try later today and let you know how I made out.

---

