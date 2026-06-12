---
title: "raxml ?"
date: 2008-03-01
forum: Education &amp; Science
---

### Post by querent on 2008-03-01
hey guys (gender-nonspecific),

is anyone using raxml for tree building in ubuntu?  where to get/how to install?

keywords: bioinformatics, phylogenetics

q

---

### Post by stamatak on 2008-03-02
Hi there,

I am the developer of RAxML, which is actually developed under ubuntu. You can get the code at my homepage (RAxML version 7.0.0)

[http://icwww.epfl.ch/~stamatak/](http://icwww.epfl.ch/~stamatak/)

Installation is fairly easy download and uncompress the source
then type "make -f Makefile.gcc" and just copy the raxml binary into
your PATH. It's all described in the Manual.

If you have a multi-core you might also consider using the Pthreads-based parallel version.

Cheers,

Alexis

PS: By the way, there are quite some RAxML users at Boulder, if you send me an email I can get you in touch with them.

---

### Post by querent on 2008-03-02
Wow.  Thanks.  I'll definitely email you later in the day.  I already know Rob Knight...I'm working under him (I'm a grad student), and it was he who suggested RAxML.

So, thanks.  I'll email you.

q

---

### Post by anudeglory on 2008-04-09
I know it's likely to be me running the Hardy Heron beta but I just cannot get RAxML to compile!?

I used the command "make -f Makefile.gcc" as suggested which just produces a long list of errors, a small selection of which is pasted below;

```
axml.c:6776: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
axml.c:6815: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
axml.c:6825: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
axml.c:6831: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
axml.c:6836: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
axml.c:6837: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
axml.c:6846: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
axml.c:6866: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
axml.c:6872: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
make: *** [axml.o] Error 1

```

Any ideas? Back to Windows then for now I guess.

---

### Post by anudeglory on 2008-04-09
Ignore the above. Major rookie error. I forgot I was on a completely fresh install and so;

```
sudo apt-get install build-essentials
```

fixed everything :)

---

### Post by anudeglory on 2008-05-22
Well, ignoring my embarrassing mistake above, I have written a small PERL script that attempts to make the use of RAxML a little easier - rather than typing in the command line options all the time.

The link is [here]("http://www.projects.ex.ac.uk/ceem/CEEM_STUDENT_PAGES_GUY.html"). 

It basically follows the instructions from the manual for doing either the Easy & Fast method or the Hard & Slow methods but with an easy to use menu interface and should nicely put results and logs into folders for you.

---

### Post by adrien214 on 2009-08-27
this is the correct link for easyRax:

[http://projects.exeter.ac.uk/ceem/easyRAx.html](http://projects.exeter.ac.uk/ceem/easyRAx.html)

---

### Post by alphaamanitin on 2011-03-24
> **stamatak said:**
>  type "make -f Makefile.gcc" and just copy the raxml binary into
your PATH. It's all described in the Manual.


Just going through the install section for the 7.04 manual and I do not see anything about copying the binary to my PATH.  Just the compiling step of it.  Could have missed it though; I have yet to read the entire manual.  

Also you mention using icc instead of gcc, is this really worth it?  I dont really know how to install icc yet.

Thanks,

AlphaA

---

