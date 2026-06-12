---
title: "kwin can't enable cover switch effect"
date: 2009-05-08
forum: Desktop Environments
---

### Post by chanyunkwan on 2009-05-08
I used to use compiz as my default WM on Kubuntu 9.04.
Today when I was switching back to KWIN, everything worked fine except the window switch effect, even I select to enable those effects in the system setting tool. 

Do any one know what's going on?

---

### Post by jeevan.joseph on 2009-06-20
I had the same problem too...

see reply by ghanarama  on [http://ubuntuforums.org/showthread.php?t=899433](http://ubuntuforums.org/showthread.php?t=899433)

Reproduced here :
Resolved it by changing the kwinrc file by hand.
To do this :

Edit the file: ```
~/.kde/share/config/kwinrc
```  


in a text editor and remove the line :

```
AltTabStyle=CDE 
```



-Jeevan

---

