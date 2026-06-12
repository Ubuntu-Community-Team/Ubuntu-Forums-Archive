---
title: "possible java problem"
date: 2006-08-06
forum: Desktop Environments
---

### Post by aineo on 2006-08-06
I am not sure the problem I am having is with java or if it is with the software application I have downloaded.  I have downloaded the Linux version of Budget Calendar from [http://www.mishell.ca/linux.html](http://www.mishell.ca/linux.html).  I was able to install this with no errors, but when I try to run the application from the command line I get the following error message:

Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Decorations

As can be expected, I cannot run the application from Applications>Office>Budget Calendar.

java -version comes back with the following:

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

When answering, keep in mind that although I have some experience with Linux, it is just enough to be dangerous and I have no background in java.  Oh, one last thing, I am running Dapper Drake.  Thanks for the help.

---

### Post by mssever on 2006-08-06
This is just a wild guess, since I have almost no experience with Java, but the error path references eclipse, which is, I believe, a Java development environment. Perhaps your program depends on Eclipse?

---

### Post by aineo on 2006-08-07
Thanks mssever, I will try to install eclipse later today.

---

### Post by bmonkey on 2006-08-07
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Decorations

that basically means that one of the classes used cannot be found. try put all ur classes in the same dir? :/

Also make sure you've imported all the libraries needed for the project

---

### Post by aineo on 2006-08-07
>try put all ur classes in the same dir? :/

Again, I am just a user of java and do not understand any of the details.  I assume that the classes would be installed via the project I am using.  If so, are you suggesting I need to find where it installed these classes at and put them all in one directory?  Sorry for the ignorance.

>Also make sure you've imported all the libraries needed for the project

According to the website I downloaded the application from it only required java, but later today I will be installing eclipse.

---

### Post by aineo on 2006-08-08
I have installed eclipse, disabled the default java install, and enabled the Sun Java install per a tutorial I found on the Ubuntu website.  Still the app is having the same error.  I have contacted the author of the app, who asked me whether eclipse was working.  It is, or at least I think it is.  I started it up from the command line by typing eclipse.  He also asked me what version of SWT eclipse was using, but I don't know how to figure this out and have not been able to find documentation as of yet.  Does anyone here have any other suggestions or can anyone tell me how to determine the version of SWT I am using?  Thanks again.

---

### Post by mssever on 2006-08-09
It would probably be most effective to work this out with the progam's author, since it appears to me to be a problem with his software. It seems to me to be bad software design to make a program depend on a development environment. At the very least, all dependencies should be listed on the website--which they aren't.

Probably he has eclipse installed on his system and forgot that other users don't.

---

### Post by aineo on 2006-08-09
As I am sure you already noticed, I have also been working with the program author.  In fact, it appears we may have solved the problem, which does appear to be an error in the code.  I was able to get the program to work last night after a little trial and error.  He is going to send an updated file that fixes the problem shortly. Although the answer didn't come from the forum, I still appreciate your time and help. Thanks.

---

