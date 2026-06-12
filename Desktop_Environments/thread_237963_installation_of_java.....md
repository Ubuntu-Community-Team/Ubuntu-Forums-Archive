---
title: "installation of java...."
date: 2006-08-17
forum: Desktop Environments
---

### Post by Mia_tech on 2006-08-17
hey guys
I'm trying to install java, but so far no luck, this is the command I'm using.
ohh by the way I enable all repositories in the resources.list file

>sudo apt-get install sun-java5-jre sun-java5-plugin

any ideas?

I'm using ubuntu 6.06

---

### Post by 23meg on 2006-08-17
What errors are you getting? Please copy and paste the complete terminal output.

EDIT: The correct package must be *sun-java5-bin*.

---

### Post by shaikhaman on 2006-08-17
I also needed jre5 and tried Mia_tech's command and got the following error:
-------------console---------------
aman@happyman:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
----------------------------------------

I think its not on the download channels...

Where i can get it ? any clue ?

---

### Post by hecato on 2006-08-17
also you can run after install

```
 update-arternatives --config java
```

Here where I learn this [http://ubuntuforums.org/showthread.php?t=235201](http://ubuntuforums.org/showthread.php?t=235201) ... (tought for 64, it should work).

---

### Post by DoktorSeven on 2006-08-17
Have you enabled **multiverse** in your sources.list?

(this is just a part of my /etc/apt/sources.list)
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

Multiverse is where the java packages are.

---

### Post by Mia_tech on 2006-08-17
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

this are my repositories, and I also tried the ones from DoctorSeven
same results.

---

### Post by Mia_tech on 2006-08-17
> **23meg said:**
> What errors are you getting? Please copy and paste the complete terminal output.

EDIT: The correct package must be *sun-java5-bin*.

jorge@ubuntu-box:/$ sudo apt-get install sun-java5-jre sun-java5-bin
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java5-bin: Depends: unixodbc but it is not installable
E: Broken packages
=================================================================

tried to install unixodbc no luck!

---

### Post by Mia_tech on 2006-08-17
oh by the way also tried the manual installation didn't work

>sudo cd /usr/java
>sudo ./jre-1_5_0_06-linux-i586.bin

---

### Post by Mia_tech on 2006-08-18
> **Mia_tech said:**
> oh by the way also tried the manual installation didn't work

>sudo cd /usr/java
>sudo ./jre-1_5_0_06-linux-i586.bin

after a tries it worked....the way to go is with the manual install, as above, didn't work for me the first time because of a permission issue.
here is the link to the java website with all the documentation, is pretty straigh forward.

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

---

