---
title: "Azureus 4.2 Java issue"
date: 2009-03-30
forum: General Help
---

### Post by Aroll605 on 2009-03-30
Hi.

I downloaded Azureus (Vuze) 4.2 and tried to run it from terminal by running 
```

lev@lev-comp:~/Desktop/vuze$ ./vuze
Starting Azureus...
Java is GCJ.. looking for Sun Java..
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest: No such file or directory
ls: cannot access /usr/java: No such file or directory
ls: cannot access /usr/lib/jvm/latest: No such file or directory
Java exec found in  /usr/lib/jvm/java-gcj/bin/
Java is GCJ.. looking for Sun Java..

```
and did not boot, obviously.

So I tried to run it directly with the java runtime environment:
```

lev@lev-comp:~/Desktop/vuze$ gij -jar Azureus2.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.common.Main
   at java.lang.Class.initializeClass(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLineParser not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:Azureus2.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)

```

I am out of ideas, could anyone help please?

Regards,

~

---

### Post by freonchill on 2009-03-30
do you have sun java installed, or a variant? (e.g. another java)
or perhaps its picky and wants a certain version of sun java, which you do not have updated...

---

### Post by Aroll605 on 2009-03-31
I do. Sun Java Runtime Environment 6 update 10 from the Ubuntu repository.

~

---

### Post by Aroll605 on 2009-03-31
bump

---

