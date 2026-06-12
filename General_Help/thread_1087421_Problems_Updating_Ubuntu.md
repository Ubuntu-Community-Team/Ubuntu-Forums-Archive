---
title: "Problems Updating Ubuntu"
date: 2009-03-05
forum: General Help
---

### Post by dnielsen515 on 2009-03-05
Hello,
I am having some problems updating, i will open up Update manager and it says i need 264 updates so i click the update button it gets 3 updates done then comes to a hault and just sits there and does nothing i have tried restarting it 5 or 6 times and the same thing over and over any answers?

---

### Post by mcla0203 on 2009-03-05
the only time i've seen it freeze is when i loose internet connection, cause it might be downloading something.  but thats not likely if it keeps occurring...

---

### Post by DougieFresh4U on 2009-03-05
Have you tried updating via terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Also, if your having problems with update manager try in terminal
```
sudo apt-get -f install
```

---

