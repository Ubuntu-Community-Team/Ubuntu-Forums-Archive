---
title: "Java, issues. (Frost Wire)"
date: 2006-10-05
forum: Desktop Environments
---

### Post by Dakaru on 2006-10-05
Ok, I installed Suns version of Java, (latest) Because that is all that my apt seemed to have. (Yes I have all repo's) So then, I proceeded to install Frostwire, which requires Java, and when I run it. It tells me I need to upgrade my java.


Is there any way to get Blackdowns version of java in apt? Or can some one please tell me how I would upgrade Suns Java when I have the latest one availaible in apt. (Synaptic)

---

### Post by IusedTObeSOMEONEelse on 2006-10-05
My personal expiriance I  installed sun java 5 & java 1.4 through add/remove and at the bottom of add/remove window I checked non-supported and supported and both java wre in add/remove. Good luck! :D

---

### Post by Jagot on 2006-10-05
Have you ensured that the one you installed is actually being used?

```
sudo update-alternatives --config java
```

---

### Post by Dakaru on 2006-10-05
> **Jagot said:**
> Have you ensured that the one you installed is actually being used?

```
sudo update-alternatives --config java
```

No I haven't ran that, yet. 

But currently I am in school. However, I will be sure to try that out when I get home.

---

### Post by javarunner on 2006-10-05
this is what I did to install JDK1.5.
Download the appropriate tar.gz from the Sun web site.
Then unpack it and place it in some directory - i used /usr/local/Java - after I created the Java directory and set the right permissions.
Then you have to set the PATH.
gedit ~/.bash_profile
Enter and save the following in this file:
export JAVA_HOME=/usr/local/Java/jdk1.5.0_09
PATH=$JAVA_HOME/bin:$PATH

Your point version of Java may not be 09.
Now log out and log in and you should be able to do this:
echo $PATH
java -version

and get what you expect.
Now you have Java anywhere and everywhere.

---

### Post by Jagot on 2006-10-05
> **javarunner said:**
> this is what I did to install JDK1.5.
Download the appropriate tar.gz from the Sun web site.
Then unpack it and place it in some directory - i used /usr/local/Java - after I created the Java directory and set the right permissions.
Then you have to set the PATH.
gedit ~/.bash_profile
Enter and save the following in this file:
export JAVA_HOME=/usr/local/Java/jdk1.5.0_09
PATH=$JAVA_HOME/bin:$PATH

Your point version of Java may not be 09.
Now log out and log in and you should be able to do this:
echo $PATH
java -version

and get what you expect.
Now you have Java anywhere and everywhere.

That's one way of doing it.  The easier way is to install the sun-java5-bin package in apt-get/aptitude/synaptic from the multiverse repo.

---

