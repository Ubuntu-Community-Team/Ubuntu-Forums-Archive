---
title: "gnash-0.8.4 configure errors: pkgs not in repositories"
date: 2008-12-04
forum: General Help
---

### Post by lotuseclat79 on 2008-12-04
I updated my repositories for Ubuntu 8.10 (from Ubuntu Intrepid User Guide), downloaded gnash-0.8.4 from the gnu website, and it appears that of 11 dependency errors (missing pkg installs during ./configure step) that 3 are not in the repositories yet:
1) libjpeg-dev
2) libungif-devel
3) libagg-dev

Anyone have any information on when if ever these pkgs will be available in the repositories, or can you recommend how to get gnash compiled?

-- Tom

---

### Post by Partyboi2 on 2008-12-05
For the  libungif-devel dependency  install libgif-dev package. 
 libagg-dev package is in the universe repo, so make sure that you have universe enabled in Software Sources.
For the libjpeg-dev dependecy try installing libjpeg62-dev package.
```
sudo apt-get install libgif-dev libagg-dev libjpeg62-dev
```

---

### Post by lotuseclat79 on 2008-12-06
> **Partyboi2 said:**
> For the  libungif-devel dependency  install libgif-dev package. 
 libagg-dev package is in the universe repo, so make sure that you have universe enabled in Software Sources.
For the libjpeg-dev dependecy try installing libjpeg62-dev package.
```
sudo apt-get install libgif-dev libagg-dev libjpeg62-dev
```
Hi Partyboi2,

Mucho thanks for the reply!

-- Tom

---

