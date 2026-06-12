---
title: "Trouble installing KDE"
date: 2009-02-23
forum: Desktop Environments
---

### Post by Abhinav1987 on 2009-02-23
I tried installing **KDE** using

**sudo apt-get install kubuntu-desktop**

but every time i get the same **error:-**



[U][I]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main openoffice.org-style-crystal 1:3.0.0-6ubuntu0intrepid1
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main openoffice.org-kde 1:3.0.0-6ubuntu0intrepid1
  404 Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-crystal_3.0.0-6ubuntu0intrepid1_all.deb](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-crystal_3.0.0-6ubuntu0intrepid1_all.deb)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-6ubuntu0intrepid1_i386.deb](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-6ubuntu0intrepid1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I][/U]

---

### Post by Dj TweeX on 2009-02-23
have you tried running the ```
sudo apt-get update
``` like it recommends?

you can also try to install it with the synaptic package manager

---

### Post by Abhinav1987 on 2009-02-23
yes it turns up the same err

---

### Post by Dj TweeX on 2009-02-23
What happens when you run the ```
sudo apt-get update
```

---

### Post by gjoellee on 2009-02-23
You are installing Kubuntu (which contains KDE), but not KDE.
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install kde -f
```

---

### Post by SuperSonic4 on 2009-02-23
KDE 4.2 and OO.o 3 don't get along. Try commenting out the sources by putting a # before them and running sudo apt-get update

---

### Post by Dj TweeX on 2009-02-23
> **gjoellee said:**
> You are installing Kubuntu (which contains KDE), but not KDE.
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install kde -f
```

i didnt even notice that. good catch

---

### Post by Abhinav1987 on 2009-02-28
Guys and Gals
All this is very interesting but all i had to do was
tick off open office from the third party software list in ubuntu tweaks and it installed just fine.
Also the error was arising because the version 3.0.0 which it was looking for had been replaced by version 3.0.1 . sorry to bug u guys should have tried it earlier.
Thnks Anyways.

---

