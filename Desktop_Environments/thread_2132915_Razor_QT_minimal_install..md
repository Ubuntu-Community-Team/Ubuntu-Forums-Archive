---
title: "Razor QT minimal install."
date: 2013-04-06
forum: Desktop Environments
---

### Post by ronizwinter on 2013-04-06
At the moment the only desktops enviroments witch can come pre installed are unity, KDE, Xfce and lxde. Although these are very good desktops what about if someone wants to use something else; like a windows manager instead? Im interested in installing Razor QT but dont want any preinsatlled packages, is there anyway i can install just base ubuntu with Razor QT with the minimal image?

I have never used the minimal .iso and just wondered if anyone would help creating a guide for installing minimal with alternate user interfaces. 

Thanks.

---

### Post by ibjsb4 on 2013-04-06
Here's some links

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=window+managers&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=window+managers&sa=Search&cof=FORID:9)
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)

---

### Post by ajgreeny on 2013-04-06
There are already threads and other sites which give you info on using the minimal install CD, so do a search on that and choose razor QT as your DE and it should be pretty easy.

Enable the razor qt ppa and you can then simply install that plus xorg, and a display manager if you wish, eg xdm or gdm or your choice.  The latter is not essential as you can always start the DE with **startx** from the command line.

---

### Post by ronizwinter on 2013-04-06
> **ajgreeny said:**
> There are already threads and other sites which give you info on using the minimal install CD, so do a search on that and choose razor QT as your DE and it should be pretty easy.

Enable the razor qt ppa and you can then simply install that plus xorg, and a display manager if you wish, eg xdm or gdm or your choice.  The latter is not essential as you can always start the DE with **startx** from the command line.

Do I use the mini.iso the alternate installer or the server edition?

---

### Post by Frogs Hair on 2013-04-06
13.04 has the razor-qt 4.1-2 session in in the repository , but I never looked for it in previous  versions.

---

### Post by ajgreeny on 2013-04-08
> **ronizwinter said:**
> Do I use the mini.iso the alternate installer or the server edition?

For the most minimal installation use the mini.iso from [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

