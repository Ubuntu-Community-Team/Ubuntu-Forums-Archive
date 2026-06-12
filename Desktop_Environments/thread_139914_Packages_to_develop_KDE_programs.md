---
title: "Packages to develop KDE programs"
date: 2006-03-05
forum: Desktop Environments
---

### Post by Harryrat on 2006-03-05
Hi there!

I am fairly new to (k)ubuntu so please forgive me if I don't see the obvious things (;

Actually I want to start writing X apps using the KDE gui. I installed those development packages (kbase-devel, kde-devel, kdelibs4-dev) but right now I still have to set those variables KDEDIR and QTDIR in order to compile programs according to the kde devel docs (ok right now refering to khello *g*).

Anything I missed yet or is it a kubuntu issue?

btw, curious: what is the difference between the packages "kde" and "kde-base"?
it looks to me right now there are two kde "branches", one generic kde and one especially designed for kubuntu...is this correct?

Thx,

Harry

---

### Post by codejunkie on 2006-03-05
[QUOTE=Harryrat]Hi there!

I am fairly new to (k)ubuntu so please forgive me if I don't see the obvious things (;

Actually I want to start writing X apps using the KDE gui. I installed those development packages (kbase-devel, kde-devel, kdelibs4-dev) but right now I still have to set those variables KDEDIR and QTDIR in order to compile programs according to the kde devel docs (ok right now refering to khello *g*).

Anything I missed yet or is it a kubuntu issue?

btw, curious: what is the difference between the packages "kde" and "kde-base"?
it looks to me right now there are two kde "branches", one generic kde and one especially designed for kubuntu...is this correct?

Thx,

Harry[/QUOTE]

kde-base and kde are meta packages ```
kde-base
``` is the core set to get up and running and ```
kde
```install's pretty much all the kde packages.

---

