---
title: "How to port an installed app from desktop to laptop"
date: 2009-01-03
forum: General Help
---

### Post by sourcecode on 2009-01-03
I have a desktop running Gutsy & a laptop running Hardy.

Sometime back I had installed Sun's JDK on my desktop using apt-get . Now , I wnt to have the same on my lappy . Is there a way I can make an installation package of the already existing JDK on the desktop , and then use it for installing on my lappy . 

Since I aleady downloaded it onto my desktop , I don't want to waste my bandwith by downlading it again on my lappy

thnx
Source

---

### Post by Tim Sharitt on 2009-01-03
you may be able to use the package you downloaded for your desktop if you haven't cleared out apt's cache since you installed it. look for a sun-java package in /var/cache/apt/archives.

---

### Post by sourcecode on 2009-01-03
Thnx , but the cache seems to be cleared . It's empty

BTW ,  I found a java installation in /usr/lib/jvm . Can I copy it as it is to my laptop ?


thnx
Source

---

