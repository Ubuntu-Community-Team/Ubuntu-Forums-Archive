---
title: "How to install Java?"
date: 2009-02-02
forum: General Help
---

### Post by mavix on 2009-02-02
Because I have dial-up, I can't use the apt-get to download Java. So I recently downloaded the .deb's for OpenJDK from using a different PC, and tried to install them on my computer. This resulted in the irritating and annoying and stupid error described below. So I thought I would try Sun's Java. So today I managed to get it, and the same problem appears! The problem is this: 
1. I run the install for sun-java6-bin.
2. Error: Dependency is not satisfiable: sun-java6-jre
3. I think: Ok cool, I need to install the other one first.
4. I run the install for sun-java6-jre
5. Error: Delendency is not satisfiable: sun-java6-bin!

Now how on earth must I install Java if two packages I am trying to install depend on each other?
Please help!

---

### Post by taurus on 2009-02-02
If those files are in .deb, you could install them from a terminal with

Applications -> Accessories -> Terminal
```
cd ~/Desktop  <-- Assuming that is where you've saved them!
sudo dpkg -i *.deb
```

---

### Post by mavix on 2009-02-03
That worked, thanks!

---

