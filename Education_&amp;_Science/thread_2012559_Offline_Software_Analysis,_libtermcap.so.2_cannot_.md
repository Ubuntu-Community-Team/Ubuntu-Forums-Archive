---
title: "Offline Software Analysis, libtermcap.so.2: cannot open"
date: 2012-06-29
forum: Education &amp; Science
---

### Post by Soonick on 2012-06-29
Hello everybody!
I am trying to install the OSA data analysis program (Offline Software Analysis, from the Integral Science Data Center: [http://www.isdc.unige.ch/integral/analysis#Software](http://www.isdc.unige.ch/integral/analysis#Software)).

However, when I try the test command (**make test**), the terminal returns the following error:

```

>>>>> Run the analysis script ...


/home/nedu/soft/osa_sw-9.0
/home/nedu/soft/osa_sw-9.0//bin/og_create:  error while loading shared libraries: libtermcap.so.2: cannot open  shared object file: No such file or directory
cd: 178: can't cd to /home/nedu/soft/osa_sw-9.0/run/obs/osatest
/home/nedu/soft/osa_sw-9.0//bin/ibis_science_analysis:  error while loading shared libraries: libtermcap.so.2: cannot open  shared object file: No such file or directory


>>>>> The analysis script terminated with return code: 127


***** Error: expected return code: 0
             -> Abort the test run at this point


```

Do you know what it could be?
Thanks in advance!

---

### Post by drmrgd on 2012-06-29
It looks like you're missing a library.  Try installing the libncurses5-dev package (I think libtermcap.so.2 is in there):

```
sudo apt-get install libncurses5-dev
```

Then try recompiling the OSA package.

---

### Post by Soonick on 2012-06-29
Thanks!

However, when I try to install the library, the terminal says that it is already updated to the most recent version...
So, the problem has to be different...

---

### Post by drmrgd on 2012-06-29
> **Soonick said:**
> Thanks!

However, when I try to install the library, the terminal says that it is already updated to the most recent version...
So, the problem has to be different...

Hmmm...I may have the wrong package, then.  I wan't quite sure the library was in the package I suggested (although I really thought it was).  On my system, I don't see that library even though I have libncurses5 and libncurses5-dev installed.  

I did a quick package search, and found some hits:

[http://packages.ubuntu.com/search?searchon=contents&keywords=libtermcap&mode=filename&suite=precise&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libtermcap&mode=filename&suite=precise&arch=any)

I'm not sure about your architecture and your setup.  Also, none of them specifically say libtermcap.so.2 (and I do have libtermcap.so on my system already).  So this might be a bit of a witch hunt, but I'm thinking it might get you close.

---

### Post by Soonick on 2012-06-29
Thanks again.
I have Ubuntu 10.04 on a 64bit machine.
There are many packages in the link that you posted, but I can not distinguish between them...

---

### Post by Bachstelze on 2012-07-01
There is no libtermcap.so.2 in Ubuntu, you will need to compile the software from source.

---

### Post by Soonick on 2012-07-02
Hi Bach, thank you.
Are you sure that I can not install the program from the binary?
I am a new, but I can try to compile the software following the official guide.
What is the main problem that I will encounter doing that?

Bye!

---

### Post by ramreddy502 on 2013-04-22
hi
i am trying to generate models for speech database using HMM, for this i am using festvox tools and speech tools.
with these tools i have completed labelling for the speech files.

now i am trying to generate F0 for speech file, but it is showing an error like  "loading shared libraries:libtermcap.so.2 can not open shared object file:no such file or directory"
 
 but libtermcap.so.2 is present in usr/lib.

please can anyone help me 

thanks in advance

---

