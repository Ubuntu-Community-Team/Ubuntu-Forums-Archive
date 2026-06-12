---
title: "Ubuntu/kubuntu repositories"
date: 2005-07-20
forum: Desktop Environments
---

### Post by linuxeiro on 2005-07-20
I have ubuntu 5.04 and now I have installed the kubuntu desktop. Do I have to change/add the files repositories? which are the official repositories for ubuntu/kubuntu, and how can I add them up to my sources.list? thank you

---

### Post by t2kburl on 2005-07-20
keep all the Ubuntu repositories. Add these for KDE 3.4.1 and some extra KDE apps & updates:

```
deb http://kubuntu.org/hoary-kde341/ hoary-updates main

deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main
```

---

### Post by arunsub on 2005-07-20
[QUOTE=t2kburl]keep all the Ubuntu repositories. Add these for KDE 3.4.1 and some extra KDE apps & updates:

```
deb http://kubuntu.org/hoary-kde341/ hoary-updates main

deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main
```[/QUOTE]

What's in dinton repos?

---

### Post by FLeiXiuS on 2005-07-20
[QUOTE=linuxeiro]I have ubuntu 5.04 and now I have installed the kubuntu desktop. Do I have to change/add the files repositories? which are the official repositories for ubuntu/kubuntu, and how can I add them up to my sources.list? thank you[/QUOTE]
 Adding repo's will enable you to a bunch more files.  I'd reccomend adding them as soon as you can :-P.  

Be sure to check out the how-to on [www.ubuntuguide.org](www.ubuntuguide.org).

---

