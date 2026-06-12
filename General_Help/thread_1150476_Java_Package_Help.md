---
title: "Java Package Help"
date: 2009-05-06
forum: General Help
---

### Post by krnekhelesh on 2009-05-06
Hi,

I am using Ubuntu 8.10. I installed Java Compiler 1.6 recently, and everything is going smooth like compiling a java file using the java compiler **javac**.Now, I need to set the Classpath for a class file. And I have tried all sorts of things but I cant figure out how to do it.

The class files are present in **/home/nik/packages**. How do I set the Classpath variable?

The Java file uses the following packages using
**import packages.graphics.JPlot2D;**

---

### Post by krnekhelesh on 2009-05-06
Anyone???

---

### Post by krnekhelesh on 2009-05-08
Thanks for you help very much.

---

### Post by ape on 2009-05-08
If the class files are just plain class files (i.e *.class), then running

    java -cp .:/home/nik/packages <class to run>

or, if compiling:

   javac -cp .:/home/nik/packages <.java file to compile>


If your class files are packaged into a .jar file, then you would need to add the .jar file into the classpath definition. i.e:

  java -cp .:/home/nik/packages/myClasses.jar <class to run>


Hope this helps.

Steve

---

