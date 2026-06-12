---
title: "KDE4 alpha 1...repository doesn't work"
date: 2007-05-11
forum: Desktop Environments
---

### Post by secret_force on 2007-05-11
The repository **deb [http://kubuntu.org/packages/kde4-3.90.1/](http://kubuntu.org/packages/kde4-3.90.1/) ./** doesn' t work...everytime I try to upgrade konsole comes up with the following message
[I]
Ophalen van [http://kubuntu.org/packages/kde4-3.90.1/./Packages.gz](http://kubuntu.org/packages/kde4-3.90.1/./Packages.gz) 404 Not Found is mislukt 
[/I]

It probably can't find the file or something

Is there another repository I can use?

---

### Post by Vojtin on 2007-05-11
same problem

---

### Post by firephoto on 2007-05-11
I changed mine to this and it seemed to work.

deb [http://kubuntu.org/packages/kde4-3.90.1/](http://kubuntu.org/packages/kde4-3.90.1/) feisty main

---

### Post by secret_force on 2007-05-11
> **firephoto said:**
> I changed mine to this and it seemed to work.

deb [http://kubuntu.org/packages/kde4-3.90.1/](http://kubuntu.org/packages/kde4-3.90.1/) feisty main

After installing the Jonathan Riddel Key 
```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

it did indeed worked...thanks

---

