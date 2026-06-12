---
title: "Run Programs From Anywhere"
date: 2008-12-03
forum: General Help
---

### Post by Setya on 2008-12-03
Hi all,

I need to run certain program from any folder where I'm currently in, AFAIK I can do this by using 'update-alternatives' command for example :

```

sudo update-alternatives --install /usr/bin/java java Programs/jdk1.6.0_07/jre/bin/java 300

```
With above command I hope I can invoke 'java -version' from anywhere, but everytime I invoke it, Xubuntu always throws the following message : 

```

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * cacao
 * openjdk-6-jre-headless
 * jamvm
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

```
Is there any steps that I'm missing ?

Any help would be greatly appreciated

Regards,

Setya

---

### Post by taurus on 2008-12-03
Did you unpack the java package in ~/Programs/jdk1.6.0_07/?  What if you run this from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by albandy on 2008-12-03
You don't have java package installed, so if you installed it manually you have to do a bit of manual configuration like linking the binaries.

If you want the sun jdk package install it this way:

sudo apt-get install sun-java6-jdk

---

### Post by Setya on 2008-12-03
Hi,

Thanks for all your quick responses.

I already have my own JDK exploded somewhere in my home directory and I just want to call it from anywhere I want. I don't want to install any new JDK provided by Ubuntu repositories.

Here's the result of calling 'update-alternatives --config java' :

```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    Programs/j2sdk1.4.2_15/jre/bin/java
*+        2    Programs/jdk1.6.0_07/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

Apparently everything is OK, but I still can't invoke 'java'.

FYI, I just migrated from Fedora and it worked as expected back then.


Regards,

Setya

---

### Post by taurus on 2008-12-03
Try linking to it with

```
sudo ln -s /home/<your_username>/Programs/jdk1.6.0_07/jre/bin/java /usr/local/bin/java
java -version
```
Assuming you've unpacked it in your $HOME/Programs.

---

### Post by Setya on 2008-12-03
Hi,

> **taurus said:**
> Try linking to it with

```
sudo ln -s /home/<your_username>/Programs/jdk1.6.0_07/jre/bin/java /usr/local/bin/java
java -version
```
Assuming you've unpacked it in your $HOME/Programs.

Thanks, but it's still not working.

FYI, I also want to be able to switch between JREs easily so using 'ln' is not an option.


Regards,

Setya

---

### Post by Setya on 2008-12-03
Well, anybody ?

---

