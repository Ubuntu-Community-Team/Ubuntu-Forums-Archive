---
title: "Desparately want normal scrollbars"
date: 2012-02-11
forum: Desktop Environments
---

### Post by kjacobs on 2012-02-11
Hello all,

I have been using XFCE desktop in Ubuntu 11.10 for a while now and really like the overall feel. The one and only thing that really bugs me is the hidden scrollbars on the right and bottom.

Is there any way to get real, normal scrollbars back for this desktop environment? Something that does not hide and is there all the time??? I sure hope so....and thanks in advance......

Ken

---

### Post by winh8r on 2012-02-11
quick search engine query turned this up:

[http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars]("http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars")


hope it helps you in some way.

---

### Post by aeronutt on 2012-02-11
This worked for me:

```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

---

### Post by kjacobs on 2012-02-12
> **aeronutt said:**
> This worked for me:

```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

Tried this and still have hidden scrollbars. Thing is....T-Bird and Firefox have normal everyday scrollbars, the rest of the OS has the hidden style. I looked at the other thread and saw a dozen different efforts....LOL, but nothing conclusive or simple. Any other thoughts????

---

### Post by kjacobs on 2012-02-12
Ooops....actually that did work Aeronutt. I had to restart and then it took affect. A huge thank you.....ahhhhhhh real scrollbars again. Whew!

Ken

---

