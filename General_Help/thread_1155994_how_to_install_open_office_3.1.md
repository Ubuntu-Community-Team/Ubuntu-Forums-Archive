---
title: "how to install open office 3.1"
date: 2009-05-11
forum: General Help
---

### Post by muctadir on 2009-05-11
i downloaded open office from softpedia. the file is a tar.gz file. 

i want to know how to install it in detail.. 
i have 2.4 installed.

need help...........

---

### Post by soro2005 on 2009-05-11
You best install it from the ppa maintained by the people who package openoffice for ubuntu. Go here: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by nbo10 on 2009-05-11
Unzip the tar file. and then from a terminal 
 >> cd DEBS/
 >> sudo dpkg -i *.deb

---

### Post by slumbergod on 2009-05-11
I had a painless, perfect upgrade using the repo above. Definitely, the easiest way!

---

### Post by cocolocko on 2009-05-11
> **soro2005 said:**
> You best install it from the ppa maintained by the people who package openoffice for ubuntu. Go here: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Works Perfecto!
Thanks

Greetings

---

### Post by sim909 on 2009-05-11
If I try to update from OOo 3.0.1, currently installed and working, using the ppa, synaptics tells me that some packages, including language-support-en and language-support-translations-en, need to be removed. 

Why is this? From the name I would say that they are not specifically for OOo.

I am not confortable removing them, fearing that this will break the functionality of some other part of the system.

Can anybody "confort" me on why these packages need to be removed and that it is a safe process?

Thank you

---

