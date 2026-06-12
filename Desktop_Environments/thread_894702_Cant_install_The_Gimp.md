---
title: "Cant install The Gimp"
date: 2008-08-19
forum: Desktop Environments
---

### Post by Sjellest on 2008-08-19
Hi :)
I've been on vecation for 2 weeks and when i came home there were some updates i needed to do and for some reason gimp has been removed. I tried to reinstall the gimp using Add/Remove but got the following error:

[COLOR="DimGray"][INDENT]Cannot install 'gimp'

This application conflicts with other installed software. To install   'gimp' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/INDENT][/COLOR]

Then i tried to install The Gimp usin Synaptic Package Manager and it said:
[INDENT][COLOR="DimGray"]gimp

  Depends: libgimp2.0 (>=2.4.6) but 2.4.5-1ubuntu2 is to be installed
  Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed
[/COLOR][/INDENT]

Then i installed libgimp2.4.6 and libpango1.20.5 and it still says the the same when i try to install Gimp...
 
So what am i suppose to do? I'm not new to ubuntu but i have never really haved troubles with it...
I hope someone can help me, and i hope everything makes sense because my english isn't perfect :)

---

### Post by Potatoj316 on 2008-08-19
I think you probably somehow installed a package that was an older version of one of the packages the GIMP requires which removed the newer version and therefore GIMP.  Try this, it worked for me when I had that problem
```
sudo aptitude install gimp
```
yes use aptitude, I tried the same thing with apt-get, synaptic, and then aptitude and only aptitude worked.  It will probably tell you that something is going to be removed, if you dont want it than remove it, if you want it well then i guess you dont have GIMP

---

### Post by Sjellest on 2008-08-19
It worked :) Thank you very much, the problem was xsane, if anyone else ever get this problem :)

---

