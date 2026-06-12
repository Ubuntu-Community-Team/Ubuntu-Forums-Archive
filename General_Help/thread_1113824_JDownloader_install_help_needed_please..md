---
title: "JDownloader install help needed please."
date: 2009-04-02
forum: General Help
---

### Post by toejamfootball on 2009-04-02
I have downloaded and unzipped all the files and have the jd.sh script in the unzipped folder. I have run the chmod command. But now when I type  ```
./jd.sh
``` I get - ```
JD Installation found: No valid JDownloader.jar exist!
Start JD-Updater
Exception in thread "main" java.lang.NoClassDefFoundError: jd.update.Main
   at java.lang.Class.initializeClass(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: com.sun.java.swing.plaf.windows.WindowsLookAndFeel not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jdupdate.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81
```

I would like to try JDowloader as I need to Schedule my downloads so they will only download in my Off-peak Bandwidth times.

I have Sun Java 6 Runtime installed.

Thanks !

---

### Post by kpkeerthi on 2009-04-02
You need sun-jre or open-jdk for this to work.
See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for install instructions

---

### Post by toejamfootball on 2009-04-02
> **kpkeerthi said:**
> You need sun-jre or open-jdk for this to work.
See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for install instructions
Thanks for the quick response! Will try this now.

EDIT: Well, I already have Sun Java Runtime Environment, but I am trying open-jdk now.

---

### Post by toejamfootball on 2009-04-02
> **toejamfootball said:**
> Thanks for the quick response! Will try this now.

EDIT: Well, I already have Sun Java Runtime Environment, but I am trying open-jdk now.
I got open-jdk and it worked! I wonder why it wouldn't work with the Sun Java though?

Thank you so much.

---

### Post by kpkeerthi on 2009-04-02
Was your Sun JRE the default JVM on your PC? The link I posted earlier has instructions on how to set default JVM.

---

### Post by toejamfootball on 2009-04-02
> **kpkeerthi said:**
> Was your Sun JRE the default JVM on your PC? The link I posted earlier has instructions on how to set default JVM.
Possibly not, I will have a look. Thanks again mate.

---

### Post by binbash on 2009-04-02
make sun's java default with sudo update-java-alternatives -s command

---

