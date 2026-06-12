---
title: "Trying to run a .deb-exe file. Install/run help?"
date: 2009-05-08
forum: General Help
---

### Post by blazingnikons on 2009-05-08
Hello!

I'm trying to run the Debian version of a chiptune tracker called "LittleGPTracker" or "LGPT" for short.  This is the package:
[http://www.littlegptracker.com/lgpt_DEB.rar]("http://www.littlegptracker.com/lgpt_DEB.rar")

And here is the documentation:
[http://wiki.littlegptracker.com/doku.php?id=lgpt:reference_manual]("http://wiki.littlegptracker.com/doku.php?id=lgpt:reference_manual")

And here are the instructions for installing on Ubuntu:
[http://gorehole.org/lgptWiki/doku.php?id=lgpt:ubuntu_installation]("http://gorehole.org/lgptWiki/doku.php?id=lgpt:ubuntu_installation")

I've downloaded, extracted, and now have to deal with a weird file in order to actually install/run the program.  The file is "lgpt.deb-exe" -- I know, right??  My problem lies in that I don't know how to install/run the lgpt.deb-exe file to get the program working.  Before someone suggests it, I've tried running it on WINE, and I've downloaded the win32 version and running that on WINE, and while the windows-esq .exe ran great for some reason I lack some essential keyboard controls.

I'm running 64-bit Intrepid on a newer laptop and regularly update. 

Anyone know the steps to get this to work?  How do I get it to work via terminal?

---

### Post by Wiebelhaus on 2009-05-08
testing.

---

### Post by ad_267 on 2009-05-08
Right click on it and change its properties so that it's executable. Then just double click on it to run it.

Or in a terminal:
```

chmod +x lgpt.deb-exe 
./lgpt.deb-exe

```

---

### Post by Wiebelhaus on 2009-05-08
> **ad_267 said:**
> Right click on it and change its properties so that it's executable. Then just double click on it to run it.

Or in a terminal:
```

chmod +x lgpt.deb-exe 
./lgpt.deb-exe

```

And works very well.

---

### Post by blazingnikons on 2009-05-08
.....Oh that was embarrassingly easy.......

Thanks!!!

---

### Post by johngilda87 on 2009-08-24
ah easy in solution :popcorn:

---

