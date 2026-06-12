---
title: "Can't find sun-j2re1.5"
date: 2005-09-27
forum: Desktop Environments
---

### Post by sachi on 2005-09-27
Hi, guys

I want to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox.  I follow the instructions in the ubuntu starter guide, trying to apt-get a package called sun-j2re1.5.

However, I couldn't find the package.  Are you able to find one?  Is there any other options?

Thanks

Sachi

---

### Post by bored2k on 2005-09-27
>  1. [http://www.google.com/url?sa=U&start=1&q=http://java.sun.com/j2se/1.5.0/download.jsp&e=9797](http://www.google.com/url?sa=U&start=1&q=http://java.sun.com/j2se/1.5.0/download.jsp&e=9797)
2.
Download Linux self-extracting file jre-1_5_0_04-linux-i586.bin 15.83 MB
3.
sudo apt-get install fakeroot java-package
4.
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
5.
sudo dpkg -i *.deb (whatever the newly Sun- DEBian package is named).
Should work.

---

### Post by Dolphin on 2005-09-27
Why is it no longer on the repositories?

---

### Post by Gustav on 2005-09-28
[QUOTE=Dolphin]Why is it no longer on the repositories?[/QUOTE]
There were some legal issues.

---

### Post by Dolphin on 2005-09-28
[QUOTE=Gustav]There were some legal issues.[/QUOTE]

Such as?

---

### Post by Unit #134679 on 2005-09-28
I dont think it matters. As long as that method works

---

### Post by Jenda on 2005-09-28
It doesn't work for me. I don't understand. Can anyone please help me interpret this?
> jenda@niniel:~$ fakeroot make-jpkg /home/jenda/Desktop/jre.bin
Creating temporary directory: /tmp/make-jpkg.XXXXhhhWMr
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

I don't think a deb file was produced.

---

### Post by GTvulse on 2005-09-28
[quote=Jenda]It doesn't work for me.[/quote]
Don't play with long paths. Operate in **one single directory**.

---

### Post by GTvulse on 2005-09-28
[QUOTE=Dolphin]Such as?[/QUOTE]
Such as the Sun's license that prohibits redistribution along other implementations of the JVM, such as GNU GCJ 4.x and Blackdown Java, both of which are available in Ubuntu's repositories. Before you ask: GCJ is required for OpenOffice.org 2.x and Blackdown is a perfectly good implementation of Java 1.4.x; in fact, I've read repeatedly claims that it is faster than Sun's  but I don't have hard data available to support such claims.

---

### Post by Gustav on 2005-09-28
[QUOTE=Dolphin]Such as?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=67198](http://ubuntuforums.org/showthread.php?t=67198)

Edit: I'm too slow :)

---

