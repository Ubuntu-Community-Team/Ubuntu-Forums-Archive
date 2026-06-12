---
title: "Something wrong with Java"
date: 2006-08-06
forum: Desktop Environments
---

### Post by zugu on 2006-08-06
If I do: ```
java -version
``` I get ```
java version "1.4.2"

```, but if I go to [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) to test my Java installation it says I have Sun's Java 1.5.0_06 installed.

Now what is the java version installed on my system? I used only the packages in the repositories.

I cannot run java files either. I googled around with the error message, only to find out that there's something wrong with the GTKToolkit I have on my system. Either it can't be found or it is an incompatible version for the Java JDK I'm using.

Anyone help?

---

### Post by sir_mud on 2006-08-06
sudo update-alternatives --config java
choose Sun's Java, should be '3'
that should fix your problem

---

