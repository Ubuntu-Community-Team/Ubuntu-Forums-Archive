---
title: "xfce not installing apt-get error?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by whisper on 2005-12-09
hello when i try to install xfce in ubuntu via the commmand ```
sudo apt-get install xubuntu-desktop
``` it will stop and say > E:couldn't find package xubuntu-desktop any suggestions and i am connected to the internet :rolleyes:

---

### Post by Crazy Man on 2005-12-09
Have you uncommented the "universe" repository lines in your sources.list (/etc/apt/sources.list)?

---

### Post by whisper on 2005-12-09
[QUOTE=Crazy Man]Have you uncommented the "universe" repository lines in your sources.list (/etc/apt/sources.list)?[/QUOTE]
dont think so how do i do that ?

---

### Post by mustang on 2005-12-09
[QUOTE=whisper]dont think so how do i do that ?[/QUOTE]

Here ya go:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by whisper on 2005-12-09
[QUOTE=mustang]Here ya go:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]
ok thats sort of confusing but when i can be bothered i will boot up and try that thanks;)

---

### Post by Crazy Man on 2005-12-09
If you're not in X (and I'm assuming you're not if you're going from a server install) try the following:

```
sudo nano /etc/apt/sources.list
```

and uncomment the repositories that contain the term "universe" (they would the ones with a "#" at the beginning. I also recommend adding the word "multiverse" to the end of those repositories to ensure greatest package selection).

---

### Post by whisper on 2005-12-09
[QUOTE=Crazy Man]If you're not in X (and I'm assuming you're not if you're going from a server install) try the following:

```
sudo nano /etc/apt/sources.list
```

and uncomment the repositories that contain the term "universe" (they would the ones with a "#" at the beginning. I also recommend adding the word "multiverse" to the end of those repositories to ensure greatest package selection).[/QUOTE]
how do i uncomment them 

sorry im a n00b:razz:

---

### Post by Crazy Man on 2005-12-09
Get rid of the "#"

and it's fine. We were all n00bs once. ;)

---

