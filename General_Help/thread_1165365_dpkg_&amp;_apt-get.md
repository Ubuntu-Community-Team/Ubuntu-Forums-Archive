---
title: "dpkg &amp; apt-get"
date: 2009-05-20
forum: General Help
---

### Post by Ghost M.D on 2009-05-20
hi guys

I want to ask

what is the diff. between dpkg & apt-get

---

### Post by Joeb454 on 2009-05-20
dpkg is the package installer, apt is the package manager.

If you had a .deb file on your desktop, to install with dpkg you would run ```
sudo dpkg -i ~/Desktop/myfile.deb
```

Basically, apt-get downloads and installs the files from the repositories, and (I think) uses dpkg to install the files :)

---

### Post by Ghost M.D on 2009-05-20
Immmm

apt-get download & install

dpkg for do not download but install

ok

---

### Post by SentientFluid on 2009-05-20
> **Ghost M.D said:**
> 
if I install a program pakage by dpkg

how I can remove it..?

```
sudo dpkg -r ~/Desktop/myfile.deb
sudo dpkg --remove ~/Desktop/myfile.deb
```

Either of the lines above will remove the package.

---

### Post by mcduck on 2009-05-20
> **Ghost M.D said:**
> Immmm

apt-get download & install

dpkg for do not download but install

ok

you put question in my head

if I install a program pakage by dpkg

how I can remove it..?

With dpkg, apt-get, Synaptic, or any other package management tool. As long as everything you install comes in .deb packages it will be recognized by Ubuntu's package management tools just like the stuff you install from repositories (which comes in .deb packages as well).

---

