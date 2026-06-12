---
title: "Compiling error."
date: 2005-03-15
forum: Desktop Environments
---

### Post by totalshredder on 2005-03-15
Hey ya'll

  I'm working on setting up HPLIP (the printing stuff for linux) and when doing a "make install" It seems to work for a long time, giveing me hundreds of these:

```
gzip: /usr/share/ppd/HP/HP-PhotoSmart_P1315-pcl3.ppd.gz already has .gz suffix -- unchanged
``` 

But then it suddenly errors out with this message:

```
make[3]: *** [install-foomatic] Error 2
make[3]: Leaving directory `/home/luke/hplip-0.8.8/prnt/hpijs'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/luke/hplip-0.8.8/prnt/hpijs'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/luke/hplip-0.8.8/prnt/hpijs'
make: *** [install-recursive] Error 1
``` 

What do I need to do? Thanks Fellas!

Luke

---

### Post by alastair on 2005-03-15
The error source appears to be above the lines you printed unfortunately. Where is the first error?

---

### Post by totalshredder on 2005-03-15
[QUOTE=alastair]The error source appears to be above the lines you printed unfortunately. Where is the first error?[/QUOTE]

There is no first error, it just goes from the first line I showed you to the errors I got. If there are more errors, I cant see them, because there is so much text it makes it so I can't see anymore. Strange.

Lucas

---

### Post by alastair on 2005-03-15
OK - then try piping the output of "make install" (or whatever) to a text file i.e.

make install 2>&1 |  tee OUTPUT

and then look at "OUTPUT".

---

