---
title: "J2SE Which one?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by cobbweb on 2006-02-16
Hey, 
  I program in Java and am trying to download and install the newest J2SE so I can compile in Linux. Is this the correct link to download that J2SE

[https://jsecom16.sun.com/ECom/EComActionServlet;jsessionid=A5B31FE201EA743DF13D7A7A866B7DBF]("https://jsecom16.sun.com/ECom/EComActionServlet;jsessionid=A5B31FE201EA743DF13D7A7A866B7DBF")

Im a little confused one if that is the correct one to download so i can programm in java. Also, does anyone have link to a good tutorial on installing? ...Correctly? lo l Thanks any help is wanted, 
  Cobbweb

---

### Post by Leif on 2006-02-17
try one of these two methods :

[http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories_26.html](http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories_26.html)
[http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories.html](http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories.html)

---

### Post by kaamos on 2006-02-17
Simple way to install the sun sdk. Open a terminal and
```
sudo su
echo "deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free" >> /etc/apt/sources.list
apt-get update
apt-get install sun-j2sdk1.5
exit

```
now that it is installed, lets starts using it
```
sudo update-alternatives --config java
```
choose sun. Then test
```
javac -version
```

---

