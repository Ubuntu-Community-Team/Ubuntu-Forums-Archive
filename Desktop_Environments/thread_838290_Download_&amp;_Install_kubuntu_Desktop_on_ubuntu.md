---
title: "Download &amp; Install kubuntu Desktop on ubuntu"
date: 2008-06-23
forum: Desktop Environments
---

### Post by zeeqy on 2008-06-23
Hi,
I m newbie, recently moved from windows platform, I downloaded and installed ubuntu, working like charm, but now I want to download and install kubuntu desktop with KDE4 but when I look at the download page it shows so many files and I really have no clue which file need to be downloaded, isnt there a way to download the whole package at once and install it?

I m on intel PC by the way

---

### Post by Sef on 2008-06-23
Download [Kubuntu]("http://kubuntu.org/download.php").

Choose either version of Hardy Heron.

---

### Post by Zorael on 2008-06-23
[http://kubuntu.org/download.php#remix](http://kubuntu.org/download.php#remix) for the KDE4 remix mirrors. (The Europe, Germany, England choices.)

You can install this alongside Gnome by just tagging the package **kubuntu-kde4-desktop** for installation in Synaptic, or via equavilent terminal commands.
```
$ sudo aptitude install kubuntu-kde4-desktop
```

---

### Post by pmlxuser on 2008-06-23
just do 
$ sudo apt-get install kde4
assuming you have a good internet connection that will install the most stable version of KDE 4 plus all the dependency.

or go to the KDE site and download something like KDE4-stable version

---

