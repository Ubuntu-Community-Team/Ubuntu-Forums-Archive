---
title: "Xine instalation: zlib needed"
date: 2005-02-25
forum: Desktop Environments
---

### Post by creilar on 2005-02-25
When I do the ./configure it says: zlib needed . I read it needs zlib libraries, what I file do I need?

---

### Post by niaz69 on 2005-03-06
I am also having the same problem, Could someone please help. 
Thank you.

---

### Post by WW on 2005-03-06
I don't know if these are what you need, but you could try installing the packages **zlib1g** and **zlib1g-dev**.

If you are going to install from source, it might be a good idea to start up Synaptic, and use the Search feature to find packages that will provide the libraries that ./configure reports as missing.  I found the above packages (and several more) by searching for "zlib".  Often you will need to install something like lib* and lib*-dev.

---

### Post by niaz69 on 2005-03-06
zlib1g and zlib1g-dev are installed according to Synaptic but i still get the same error when i run ./confure.

---

### Post by olavjunior on 2007-02-21
Uuuh - haven't anybody solved this problem since march 05? Buhuu
Having exactly the same problem!

---

### Post by yoroto on 2008-02-07
just install zlib-devel from [www.zlib.net](www.zlib.net)

---

### Post by 620 on 2008-05-17
```
sudo apt-get install zlib1g-dev
```

it works for me :)

After 3 years and a couple of months it solved.

---

