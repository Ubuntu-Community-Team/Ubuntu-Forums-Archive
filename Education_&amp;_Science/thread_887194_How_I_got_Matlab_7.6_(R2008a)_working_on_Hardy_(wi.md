---
title: "How I got Matlab 7.6 (R2008a) working on Hardy (with Compiz)"
date: 2008-08-11
forum: Education &amp; Science
---

### Post by tvst on 2008-08-11
I was trying to get Matlab to run on Ubuntu 8.04, but I kept getting the following error:

```
Unable to initialize com.mathworks.mwswing.MJStartup
Fatal Error on startup: Failure loading desktop class
```

After reading many forums, most of which told me to use a different Java runtime or tell Matlab to use a different toolkit, I bumped onto the solution. Open a terminal and navigate to the folder where you installed Matlab, then:

```

$ ln -s sys/java/jre/glnxa64/jre1.6.0/lib/i386/motif21 motif12
```

The name of the folder "i386" above depends on the architecture for which you installed Matlab. It could be something like "amd64", for example.

You're done! Why this works, I haven't a clue. It seems from the solution that Matlab is trying to read a folder that does not exist, so we have to tell it where to read instead. Strange... And it turns out I did not have to do anything that was written on any of the threads to make it work with Compiz.

---

### Post by paulita on 2009-01-05
Hi, i've got the same error and your solution didn't work for me... I'm ussing ubuntu Hardy but i don't have compiz working. I've noticed that when i run Matlab as root no error appears and everthing seems fine.

---

### Post by neurostu on 2009-01-28
I don't know if you ever solved this but I had the same problem after upgrading from Matlab 2007 to 2008. 

To get all the widgets to appear in 2007 I had to run:
```

export MToolkit="AWTToolkit"

```
or something like that. I deleted the environment variable and it worked fine!

---

