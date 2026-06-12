---
title: "help files missing in RKWard"
date: 2009-03-02
forum: Education &amp; Science
---

### Post by elvijs on 2009-03-02
For some reason I cannot access the help files in RKWard anymore. It was working fine earlier, so I guess it has to do with a system upgrade. I know that I can view the help files online, but it is much more convenient to do this in RKWard. Here's the error message:

```
> help(confint)
Error in print.help_files_with_topic("/usr/lib/R/library/stats/html/confint.html") : 
  No HTML help for 'confint' is available:
corresponding file is missing
```

Does anybody know how to fix this?

---

### Post by NikoC on 2009-03-03
I know there is a problem with RKward and intrepid:
[https://bugs.launchpad.net/ubuntu/+source/rkward/+bug/272527]("https://bugs.launchpad.net/ubuntu/+source/rkward/+bug/272527")
But this has to do with the menus.

You might want to reinstall rkward from source as suggested in the thread, this surely fixed my problems!

cheers,

Niko

---

### Post by earlycj5 on 2009-03-03
do you have r-base-html installed?

---

### Post by NikoC on 2009-03-04
Just checked it via synaptic and yes I have that package installed.

---

### Post by earlycj5 on 2009-03-04
> **NikoC said:**
> Just checked it via synaptic and yes I have that package installed.

I was asking the OP.

If you installed from source you wouldn't have that package installed.  You'd have to install texinfo to compile the HTML help files.

---

### Post by elvijs on 2009-03-05
> **earlycj5 said:**
> do you have r-base-html installed?

I didn't - everything works fine now. Thanks a lot!!

---

