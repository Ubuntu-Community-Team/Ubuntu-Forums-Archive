---
title: "Vlc"
date: 2006-01-14
forum: General Help
---

### Post by KhanArash on 2006-01-14
Googmorning

I am trying to install VLC player, but it says: you cant install it beacause something else will be deleted!

DO u know how I can get it installed?

---

### Post by Perfect Storm on 2006-01-14
What it want to delete?

---

### Post by 23meg on 2006-01-14
What's the exact error you're getting? Make sure you only have the Ubuntu repositories in your sources.list and type ```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by KhanArash on 2006-01-14
[QUOTE=Artificial Intelligence]What it want to delete?[/QUOTE]

It doesnt say what it want to delete...it says just that it cant be installed beacause something else will be removed.

---

### Post by KhanArash on 2006-01-14
[QUOTE=23meg]What's the exact error you're getting? Make sure you only have the Ubuntu repositories in your sources.list and type ```
sudo apt-get update
sudo apt-get install vlc
```[/QUOTE]

Følgende pakker har uinnfridde avhengighetsforhold:
  vlc: Avhenger av: liba52-0.7.4 men lar seg ikke installere
       Avhenger av: libid3tag0 (>= 0.15.1b) men lar seg ikke installere
       Avhenger av: libmad0 (>= 0.15.1b) men lar seg ikke installere
       Avhenger av: libmodplug0c2 (>= 1:0.7-4.1) men lar seg ikke installere
       Avhenger av: libmpeg2-4 men lar seg ikke installere
       Avhenger av: wxvlc men skal ikke installeres
E: Ødelagte pakker

Ødelagte pakker : means Broken files!

---

### Post by 23meg on 2006-01-14
Make sure only the official Breezy repositories are in your /etc/apt/sources.list file, and then type ```
sudo apt-get -f install
sudo apt-get update
```
Then launch Synaptic, remove all packages listed with the "Broken" filter under "Custom", then type ```

sudo apt-get install vlc
```

---

### Post by KhanArash on 2006-01-14
[QUOTE=23meg]Make sure only the official Breezy repositories are in your /etc/apt/sources.list file, and then type ```
sudo apt-get -f install
sudo apt-get update
```
Then launch Synaptic, remove all packages listed with the "Broken" filter under "Custom", then type ```

sudo apt-get install vlc
```[/QUOTE]

HOw can I ffind out if the official Breezy repositories are in my /etc/apt/sources.list??
And there are no files in "Broken" in synaptic

---

### Post by jrib on 2006-01-14
[QUOTE=KhanArash]HOw can I ffind out if the official Breezy repositories are in my /etc/apt/sources.list??
And there are no files in "Broken" in synaptic[/QUOTE]

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

