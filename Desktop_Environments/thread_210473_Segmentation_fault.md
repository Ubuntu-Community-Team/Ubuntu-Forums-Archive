---
title: "Segmentation fault"
date: 2006-07-06
forum: Desktop Environments
---

### Post by georgevn on 2006-07-06
hi
Anyone knows what happened and how to fix when a program returns "Segmentation fault" when launching?
> 
qui@georgevn:~$ qgo
Segmentation fault

thank you

---

### Post by mazirian on 2006-07-16
Same problem here.  I love the program too.  stracing it turns up all kinds of mess

---

### Post by yfh2 on 2006-09-29
Guys,

Here is qGo main developer ...
I have good news for you.
After a long hunt started by Loïc Martin, I could track down to the very cause of this crash, which seems to be 'Ubuntu specific'
(no other distro suffers from it).

The new qGo version 1.5.1 fixed it, and had been released early July. Loïc was kind enough to make a package, which you can find on qGo home page : [http://qgo.sourceforge.net](http://qgo.sourceforge.net)

Here is the direct D/L link :
[http://prdownloads.sourceforge.net/qgo/qgo_1.5.1-1_i386.deb?download](http://prdownloads.sourceforge.net/qgo/qgo_1.5.1-1_i386.deb?download)

Loïc is away from Internet now, so I posted on rgg, but someone else than me would have to make this package available within Ubuntu repositories.

Best regards

---

### Post by mazirian on 2006-09-29
Excellent news.  Installing it now.  Thanks for your efforts and the fine program.

---

