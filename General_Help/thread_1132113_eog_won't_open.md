---
title: "eog won't open"
date: 2009-04-21
forum: General Help
---

### Post by bcrook88 on 2009-04-21
I am currently running a fully updated clean install of Ubuntu Jaunty and I can't open any pictures with eog. When I run eog in a terminal I get:
```
brian@brian-laptop:~$ eog
eog: error while loading shared libraries: liblcms.so.1: cannot open shared object file: No such file or directory

```

Also, when I attempt to open jpg files in GIMP, it gives me an unknown file type error. It can open png files fine. 

I installed GQView and that works fine but I prefer eog.

Any help would be greatly appreciate and if any more info is needed please let me know.

Thanks
Brian

---

### Post by cariboo on 2009-04-21
Try in an Applications-->ACcessories-->Terminal:

```
sudo apt-get -f install
```

Just to make sure there aren't any missing dependencies.

jim

---

### Post by bcrook88 on 2009-04-21
> **cariboo907 said:**
> Try in an Applications-->ACcessories-->Terminal:

```
sudo apt-get -f install
```

Just to make sure there aren't any missing dependencies.

jim

thanks jim,
```
brian@brian-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I had already tried that but here is the output...just to be sure.

---

### Post by pnutzh4x0r on 2009-04-22
You can try to reinstall the lcms library:

```
sudo apt-get install --reinstall liblcms1
```

---

### Post by bcrook88 on 2009-04-22
> **pnutzh4x0r said:**
> You can try to reinstall the lcms library:

```
sudo apt-get install --reinstall liblcms1
```


That worked, both GIMP and eog work now!
Thank you so much, pnutzh4x0r! It seemed like such a basic problem.

Thanks everyone who helped!

---

