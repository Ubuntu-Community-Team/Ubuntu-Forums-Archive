---
title: "Compile java program"
date: 2009-05-24
forum: General Help
---

### Post by vardhan0789 on 2009-05-24
I installed java(sun-java-1.6-bin) using add/remove programs. Now   when i press javac in the terminal, it gives some packages and advices the java is may be present in those folders. Now how to compile a program

---

### Post by ActiveFrost on 2009-05-24
You need to install JDK : 
```
sudo apt-get install sun-java6-jre sun-java6-jdk
```

---

### Post by vardhan0789 on 2009-05-25
thank you.
can you help me in how to install Net Beans IDE

---

### Post by colau on 2009-05-25
> **vardhan0789 said:**
> thank you.
can you help me in how to install Net Beans IDE
From System>Administration>Synaptic ...
Search netbeans.

---

### Post by ceylonerana on 2009-05-25
To install NetBeans its better to download it from here.
[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)

Then copy it to /usr directory.

Go to the Terminal.

Change the access permissions using chmod command.

chmod u+x netbeans-VERSION-linux.sh

Then run the application 

./netbeans-VERSION-linux.sh

After few seconds the Installation dialog box will appear. You can install it using that.

Have Fun..... :D

---

