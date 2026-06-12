---
title: "Installing Software offline"
date: 2008-12-13
forum: General Help
---

### Post by hashan17 on 2008-12-13
Hello people, 
I'm interested in programing and i'm doing my developments in Windows.. But i wanna shift to Linux (Ubuntu) I don't have an interbet connection at home so i can't update my PC online. So i'm downloading software from internet cafes and insalling them to PC. But it gives lot of errors.. Pls tell me how to insall JDK, mySQL, Apache softwares offline..

Thank you !!!

[http://hashanj.blogspot.com](http://hashanj.blogspot.com)

---

### Post by bluefrog on 2008-12-13
download a ubuntu DVD to begin with. you will have access to lot of things.

---

### Post by fguilhon on 2008-12-13
Are you downloading software from a Ubuntu machine???
If so, you can issue
```
sudo apt-get install whateveryouwant
```
and the, you copy the files in:
```
/var/cache/apt/archives
```
If not, then you will have a lot a trouble if you are downloading package by package...

---

### Post by BatsotO on 2008-12-14
Yes, welcome to painful way of of ubuntu offline user.
A minute ago i found [http://offlineubuntu.co.cc/index.php](http://offlineubuntu.co.cc/index.php) 
Maybe we can give it a try, we'll still need internet connection to download packages we want, along with all of the dependencies, but i hope it will be less painful compared to dependencies nightmare when installing .deb in offline machine.

I gave up downloading repository dvd from cyber-cafe long time ago, just imagine how long will it take to complete.

---

### Post by 2hot6ft2 on 2008-12-14
> **BatsotO said:**
> Yes, welcome to painful way of of ubuntu offline user.
A minute ago i found [http://offlineubuntu.co.cc/index.php](http://offlineubuntu.co.cc/index.php) 
Maybe we can give it a try, we'll still need internet connection to download packages we want, along with all of the dependencies, but i hope it will be less painful compared to dependencies nightmare when installing .deb in offline machine.

I gave up downloading repository dvd from cyber-cafe long time ago, just imagine how long will it take to complete.
I was going to say that one and this one here take your pick [http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by BatsotO on 2008-12-14
Neat

---

### Post by hashan17 on 2008-12-15
Thanks for your help... But I'm using a Windows machine for downloading... In that case i need to download package by pacage.

---

### Post by hashan17 on 2008-12-15
Thank you... I'll try your method. I think 3G mobile will help me a litle to download things... Can you tell me what are the crirical updates we have to make? I mean do i have to install a virus guird?

---

### Post by EXCiD3 on 2009-01-01
New version of [**Keryx**]("http://keryx.betaserver.org") was released that should make everything extremely easy to do. :)

---

