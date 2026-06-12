---
title: "Ubuntu &amp; javax.comm"
date: 2006-06-11
forum: Desktop Environments
---

### Post by xenomorph99 on 2006-06-11
Hi,

I have a Java application that requires javax.comm but I cannot find it in the package manager. 

I've downloaded the Sun runtime for Mozilla so I can actually run Java apps (this is a .jar) so I'm just missing this library.

Anyone help, please?

Ta,
Xeno

---

### Post by jvictor on 2006-06-11
The communication API is not a part of the standard java distro. U need to get it seperately and make it available in the CLASSPATH. 

I remember that it was a jar file included in the calsspath , however I could not get it work at that point of time , and used c as the solution 

U can get it from

[http://www.sun.com/download/products.xml?id=43208d3d](http://www.sun.com/download/products.xml?id=43208d3d)

---

### Post by xenomorph99 on 2006-06-11
Thanks. 

I downloaded the file but have had a quick search for files containing 'classpath' and there are many..so I don't know which one to modify. Anyone assist?

Ta,
Xeno

---

### Post by jvictor on 2006-06-11
I dint get this part 
> 
I downloaded the file but have had a quick search for files containing 'classpath' and there are many..so I don't know which one to modify.

Are u telling that you tried to search for files that have classpath in it ?

CLASSPATH is an environment variable u need to set in /home/<username>/.bashrc 

you can do it by following these steps
open a terminal and type

gedit ~/.bashrc

and add these 2 lines at the end of the file 

CLASSPATH=$CLASSPATH:/home/<full_path_to_jar_including_fileName>:.
export CLASSPATH

u must replace <full_path_to_jar_including_fileName> with the actual jar files name

eg:- 
CLASSPATH=$CLASSPATH:/home/abc/java_comm3244.jar:.
export CLASSPATH

also I guess you may run into problems if you are not using Suns JDK

---

### Post by xenomorph99 on 2006-06-11
Hi,

Thanks for that - will try it.

yes, I did search for a configuration file with classpath in it.... I'm quite new to Linux but it seemed like a reasonable thing to do at the time ;)

Thanks again,
Xeno

---

### Post by xenomorph99 on 2006-06-11
Hi,

OK, I tried that. I've added the lines to bashrc then I tried to run the jar file just by right clicking on it. Needless to say, it didn't work as expected.

I then had the bright idea of running it via the command line with:

"java -jar jpl2alpha5.jar"

which yielded:

> 
Exception in thread "main" java.lang.NoClassDefFoundError: jpl2.PsionLink
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: javax.comm.SerialPortEventListener not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jpl2alpha5.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...2 more

OK, now this is largely irrelevant because I like Linux but I really can't be bothered to mess around changing n files or something just to get something to work that works in Windows 1st time without any hassle. 

Thanks for the help, though.

Ta,
Xeno

---

### Post by jvictor on 2006-06-11
1) As I said, u r running into trouble with GCJ which is not Sun's Jdk

Ist install the Sun's JDK , and then only u can go ahead...

This line shows it
```

Caused by: java.lang.ClassNotFoundException: javax.comm.SerialPortEventListener not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jpl2alpha5.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
```


2) U need to close that terminal and reopen a new one , put the  jpl2alpha5.jar in the directory where you want to execute , change directory to that and then execute 

java -jar <jar_name>

Are u new to Java too ?

Giving up just because it dint work first time is not the solution , IMHO persist for some more time . Its a different world here, with Linux, and Linux is NOT Windows .

---

### Post by xenomorph99 on 2006-06-11
> Are u new to Java too?

Yep. I don't generally have to use it nor do I have to meddle with configuration of it. The only Java application I use regularly is PVCS version control software and that is dog slow and an utter RAM hog. But, other than that, it's fine ;) 

OK, I'll look into downloading the proper files although there isn't much point as I the app I'm trying to get to run is used to talk to my Psion 5MX PDA. And, AFAIK, it can't actually sync with anything in Linux...

I don't generally give up the first time; if I really had to get it to work, I would spend the time and effort required.

Thanks for the help.

Regards
Xeno

---

### Post by xenomorph99 on 2006-06-11
OK, did as you suggested.

Now when I run it I don't get any errors.

It still doesn't work (Application says 'Please ensure javax.comm  library is installed properly)

...but no errors.

I think I'll leave it at that. :rolleyes: 

Thanks,
Xeno

---

### Post by jvictor on 2006-06-11
As u wish ! Good luck :)

---

