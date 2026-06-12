---
title: "KTechlab dependency"
date: 2006-07-18
forum: Desktop Environments
---

### Post by rgoble on 2006-07-18
I am trying to install [KTechLab]("http://ktechlab.org/download/deb/") and I am getting an error.

I am running a pretty clean install of Dapper, and the KTechLab package is for Breezey. I installed all of the required packages on that page and they all installed fine. However when i went to install the program itself I get the following error.

Error: Dependency is not satisifiable: kdelibs4c2.

Using Synaptic I installed the packages for kdelibs and kdelibs4c2a, hopeing they were what it was looking for but it still doesn't work. Also I do have the universe repos setup.

I will be greatful for any help.

---

### Post by legout on 2006-10-04
Maybe my answer comes lil late, but just install ktechlab with:

```

sudo dpkg --forece-all -i ktechlab-0.3_i386.deb

```

---

### Post by rgoble on 2006-10-12
Its never to late for an answer, especially one that works!

The package was made for Breezy and I am running Dapper so I didn't think it would work. I think I tried to install it before anyway but it wouldn't because it said it was missing the package kdelibs4c2.

Thanks for the help.

---

### Post by legout on 2006-10-13
No Prob:-D

---

### Post by rgoble on 2006-10-16
Ok I used your suggestion and it installed the package and the program ran fine. However Synaptic told me I had a broken package installed and made me remove it before it would let me do anything else. Do you have an ways to get around this? 

I am going to try and build it from the source later. I know I was getting errors before when I tried but this time i think i will try a little harder to resolve them.

---

### Post by legout on 2006-10-16
I´m sorry. I´m not a ubuntu user anymore and i only was for some weeks. So i don´t know how to get around this.

---

