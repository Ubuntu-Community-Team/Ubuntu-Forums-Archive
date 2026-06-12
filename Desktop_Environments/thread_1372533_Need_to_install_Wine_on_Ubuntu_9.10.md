---
title: "Need to install Wine on Ubuntu 9.10"
date: 2010-01-04
forum: Desktop Environments
---

### Post by balu360 on 2010-01-04
Hey guys...

i am using Ubuntu 9.10, and i have downloaded wine from 

[http://sourceforge.net/projects/wine/](http://sourceforge.net/projects/wine/)

how can i install in my PC. I don't  have internet in PC.
i have copied the "wine-1.1.33.tar" (that's the downloaded file) to my desktop of ubuntu.

pls tell me how to do it.

Am i want to use Ubuntu rest of my life.

Thanks in advance.

---

### Post by AlexDudko on 2010-01-04
Extract the archive to some directory
then **cd** to the directory. And look for install or readme files, which describe installation procedure.
If it is a source code (not a precompiled binary pachage), then you apparently will need internet connection to install required compiler and libraries, which are not installed by default.

---

### Post by balu360 on 2010-01-04
The tar file dont have any readme files..

Pls tell me how to** CD** to Directory Procedure?

is there any way to do with out internet..

---

### Post by llawwehttam on 2010-01-04
You don't really want to use the tar as you have to compile it yourself so it is made for developers and linux geeks.
It is a complicated procedure as you need to install a lot more programs such as make and gcc then use the commands ( once extracted) in the directory to make it and install it.

For Ubuntu download the latest .deb package for your platform and OS from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

( i guess your OS is i386 ) as that is the most common.

Once you have downloaded it you can just double click on it to install.

EDIT: at the moment the latest wine **[Wine 1.1.35 i386]("http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.35%7Ewinehq0%7Eubuntu%7E9.04-0ubuntu1_i386.deb") **is not working for me so use the one before.[B]

Direct link is here: [http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.34~winehq0~ubuntu~9.04-0ubuntu1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.34%7Ewinehq0%7Eubuntu%7E9.04-0ubuntu1_i386.deb")

[/B]Yes I know its the Jaunty package but it should work fine in 9.10 karmic.

---

### Post by howefield on 2010-01-04
Or do the sensible thing and add the repository. 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

This is assuming that the version in the Ubuntu repository is not sufficient for your needs ?

---

### Post by alwayshere on 2010-01-04
Now see this easy as

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by llawwehttam on 2010-01-04
> **howefield said:**
> Or do the sensible thing and add the repository. 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

This is assuming that the version in the Ubuntu repository is not sufficient for your needs ?

> **alwayshere said:**
> Now see this easy as

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

err guys... He did say he does NOT have internet access on that machine.

---

### Post by alwayshere on 2010-01-04
ok first get the net hooked up

---

### Post by alwayshere on 2010-01-04
ok jokes aside this should help ya 
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by 3Miro on 2010-01-04
Synaptic has an option to only download a package, use that and the move the package over to the new machine. You should be able to install it by clicking on it (make sure the architecture matches, i.e. both computers are either 32 or 64-bit).

---

### Post by balu360 on 2010-01-05
Thanks You all for your valuable help.

I going  try your suggestions. I will keep you update my situation..

Thanks.. God Bless you...


Ubuntu Rocks......

---

