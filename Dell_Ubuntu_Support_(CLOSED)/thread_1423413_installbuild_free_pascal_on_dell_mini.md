---
title: "install/build free pascal on dell mini"
date: 2010-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gagraf on 2010-03-06
The steps I have done are:
1. downloaded all the .deb files and began to install by right clicking file name. The documentation file (with _i386.deb) installed. fp-compiler_2.4.0-0-i386.deb failed with message: error: Dependency is not satisfiable: fp-units-rtl. Installed fp-units-rtl_2.4.0-0_i386.deb. Tried to install fp-compiler again and got same error.
2. used dpkg -l and removed documentation and units packages with dpkg -d (i think it was -d). Tried to install fp compiler and error: package architecture (i386) does not match system (lpia).
3. downloaded complete tar ball from [www.freepascal.org]("http://www.freepascal.org"). unziped and extracted the tar ball. Read README which had many makefile settings. Some settings were confusing and don't know if processor lpia is supported.
 
So now what do I do?

---

### Post by snowpine on 2010-03-06
I am not familiar with free pascal, however: This thread has some good info on how to install i386 .deb's on an lpia-architecture system:

[http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)

---

### Post by gagraf on 2010-03-07
> **snowpine said:**
> I am not familiar with free pascal, however: This thread has some good info on how to install i386 .deb's on an lpia-architecture system:
 
[http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)
 
Thanks.  I looked at the thread you suggested.  Free pascal is different than the example in the thread and free pascal is much larger and complicated.  And, I fear that building free pascal from source files is too time consumming.  
 
I am thinking that a more practical solution is to buy another computer with i386 architecture.  I read that in a few years, ubuntu will no longer support the lpia processor.
 
Or, someone with more knowlege may have a software solution.

---

### Post by snowpine on 2010-03-07
> **gagraf said:**
> Thanks.  I looked at the thread you suggested.  Free pascal is different than the example in the thread and free pascal is much larger and complicated.  And, I fear that building free pascal from source files is too time consumming.  
 
I am thinking that a more practical solution is to buy another computer with i386 architecture.  I read that in a few years, ubuntu will no longer support the lpia processor.
 
Or, someone with more knowlege may have a software solution.

You can install i386 Ubuntu on the Dell Mini, no problem. :)

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

If you have GMA500 Poulsbo graphics (mini 10 and mini 12) you might have to jump through some hoops to get the proper graphics drivers installed. :( Mini 9 and Mini 10v have GMA945 graphics which work out of the box. :)

lpia is a rather unusual Dell/Canonical architecture; most developers only release .debs for i386 and amd-64. I personally have 3 Atom computers and I'm not running lpia on any of them. You certainly don't need to buy a new computer to program in Pascal.

---

### Post by gagraf on 2010-03-07
> **snowpine said:**
> You can install i386 Ubuntu on the Dell Mini, no problem. :)
 
[http://www.ubuntumini.com/](http://www.ubuntumini.com/)
 
If you have GMA500 Poulsbo graphics (mini 10 and mini 12) you might have to jump through some hoops to get the proper graphics drivers installed. :( Mini 9 and Mini 10v have GMA945 graphics which work out of the box. :)
 
lpia is a rather unusual Dell/Canonical architecture; most developers only release .debs for i386 and amd-64. I personally have 3 Atom computers and I'm not running lpia on any of them. You certainly don't need to buy a new computer to program in Pascal.
 
Thanks for your reply.
 
Well, I have Mini 10v, Ubuntu Kernel Linux 2.6.24-22-lpia.  Do I rebuild the Kernel to obtain i386?  I need more info.

---

### Post by snowpine on 2010-03-07
> **gagraf said:**
> Thanks for your reply.
 
Well, I have Mini 10v, Ubuntu Kernel Linux 2.6.24-22-lpia.  Do I rebuild the Kernel to obtain i386?  I need more info.

i386 is the standard Ubuntu architecture. You can install it by simply following the instructions at [http://ubuntu.com](http://ubuntu.com) and you might find the link in my previous post [http://ubuntumini.com](http://ubuntumini.com) helpful for hardware tweaks.

Of course you might choose to stay with lpia if you prefer; I do not have much experience with that architecture personally.

---

### Post by RedRat on 2010-03-08
Just out of curiosity why are you compiling programs in Pascal? As an old time Borland Pascal (in the old DOS years), Pascal was pretty interesting and hot for awhile, but nowadays it seems that C and C++ are more commonly used for programing. Perhaps Free Pascal is different from the old Pascal I knew and loved.

---

### Post by gagraf on 2010-03-11
> **RedRat said:**
> Just out of curiosity why are you compiling programs in Pascal? As an old time Borland Pascal (in the old DOS years), Pascal was pretty interesting and hot for awhile, but nowadays it seems that C and C++ are more commonly used for programing. Perhaps Free Pascal is different from the old Pascal I knew and loved.

I have some Turbo Pascal 7 code that I wanted to work with.  After the above posts, I am looking at Gnu Pascal (gpc).  Looks like it will solve my needs.  The documentation is poor.  
More I work with gpc, the better it seems.

---

### Post by gagraf on 2010-03-11
> **snowpine said:**
> i386 is the standard Ubuntu architecture. You can install it by simply following the instructions at [http://ubuntu.com](http://ubuntu.com) and you might find the link in my previous post [http://ubuntumini.com](http://ubuntumini.com) helpful for hardware tweaks.

Of course you might choose to stay with lpia if you prefer; I do not have much experience with that architecture personally.

Thanks for your input.  I have some concern that I would need to work with drivers.  GNU Pascal may solve my Pascal problem.  Thus, this thread is almost solved.

This thread has led me to a "lpia problem: What is lpia?".  What are the lpia functions?  How do I call them?

---

