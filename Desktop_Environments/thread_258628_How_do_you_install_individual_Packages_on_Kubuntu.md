---
title: "How do you install individual Packages on Kubuntu"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Transport Man on 2006-09-16
Hi there. 

I have Kubuntu installed on my computer and I am wondering how I am supposed to install indivdual packages on it. I'm trying to install the Wine package which installed and worked no problems on Ubuntu but on Kubuntu I get an error saying that the package is not in my PATH. I also get similar problems when trying to install other packages that installed no problem under Ubuntu. 

Any help on this matter would be greatly appreciated.
Thanks.

---

### Post by gilgongo on 2006-09-16
How are you attempting to install these packages at the moment? I just open a terminal and type > sudo apt-get install <packagename>

---

### Post by Transport Man on 2006-09-16
Iv'e tried every possible way that I know double clicking on the file right clicking and then selecting Install Package and also using the terminal all of those options come up with the same error saying that the package is not verified and that it is not in my PATH. This is happening with more than one package and those packages also installed without a problem on Ubuntu so I don't think that there is anything wrong with the actual packages themselves.

---

### Post by artinla on 2006-09-16
try sudo dpkg -i <package name>

I am assuming that this is a .deb package and not a .gz source package.

---

### Post by Transport Man on 2006-09-16
I've tried that and it still comes up with the same error message.

---

### Post by Transport Man on 2006-09-16
oh and btw for the record the packages that I am trying to install are .deb packages

---

