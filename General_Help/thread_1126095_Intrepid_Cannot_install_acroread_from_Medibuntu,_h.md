---
title: "Intrepid: Cannot install acroread from Medibuntu, however can install skype"
date: 2009-04-15
forum: General Help
---

### Post by Ubuntooid on 2009-04-15
I've followed [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and issued such commands:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

After that I've installed Skype via

sudo apt-get install skype

but could not install Acrobat Reader:

~% sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

---

### Post by zvacet on 2009-04-15
That package is in **partner** repo.In terminal

```
gksudo gedit /etc/apt/sources.list
```

and add this line

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install acroread
```

---

### Post by Ubuntooid on 2009-04-15
> **zvacet said:**
> That package is in **partner** repo.In terminal
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


Thanks, it worked. However I still wonder what happened with acroread in Medibuntu...

---

### Post by revane on 2009-05-13
I had exactly your problem. Every forum posting said use Medibuntu but it wouldn't work. I eventually found a page from ubuntu.org that suggested going to medibuntu with a web browser and looking for packages directly would be better. When I found the acroread package, all it had was an amd64 architecture. I'm guessing that's why it won't show up with apt.

---

