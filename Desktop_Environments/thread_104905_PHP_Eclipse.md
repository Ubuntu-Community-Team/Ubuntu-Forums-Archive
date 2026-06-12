---
title: "PHP Eclipse"
date: 2005-12-17
forum: Desktop Environments
---

### Post by TudorB on 2005-12-17
Is there a .deb package for PHP Eclipse or can I add it to the repos, so I can just apt-get install it instead of compiling from the source?

---

### Post by endersshadow on 2005-12-17
Once you install Eclipse, which can be obtained via apt-get:

```
sudo apt-get install eclipse-base
sudo -k
```

You can load PHPEclipse automatically, as described [here](http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse).

---

### Post by geek.de.nz on 2006-02-11
> Once you install Eclipse, which can be obtained via apt-get:

 	Code:
 	[LEFT]sudo apt-get install eclipse-base
sudo -k[/LEFT]
 
 
You can load PHPEclipse automatically, as described [here]("http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse").

So how do I start eclipse then after I installed it like that? I cannot start with
#eclipse
bash: eclipse: command not found

---

### Post by geek.de.nz on 2006-02-12
[quote=geek.de.nz]So how do I start eclipse then after I installed it like that? I cannot start with
#eclipse
bash: eclipse: command not found[/quote] 
OK, I found it out myself. Eclipse also needs the eclipse-platform package.
#sudo apt-get install eclipse-platform
Then to install PHPEclipse you need to start as root, so
#sudo eclipse
Then you can install the PHPEclipse Plugin as described [here]("http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse")

OK, now it shouldn't be a problem to anyone anymore ;)

---

### Post by svyatogor on 2006-02-27
[QUOTE=geek.de.nz]OK, I found it out myself. Eclipse also needs the eclipse-platform package.
[/QUOTE]

I installed eclipse-platform but still cannot find that damn eclipse file to run :( there is no /usr/bin/eclipse nor anything simmilar.

---

