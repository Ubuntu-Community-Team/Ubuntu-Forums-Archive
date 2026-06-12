---
title: "openmodeller"
date: 2009-06-23
forum: General Help
---

### Post by JFDS on 2009-06-23
Hi everybody,

Please help me out with this. I am fairly new ubuntu user, and I am putting a lot of effort in trying to make things easier for me as I am not familiar with many programming and software skills. 

Does anyone know how to install openmodeller in ubuntu 9.0.4?

Thanks!

---

### Post by michy99 on 2009-06-23
There doesn't seem to be a .deb file for it, but there is a .rpm, which can be converted to .deb with alien.

First, download libopenmodeller-1.0.0-0.src.rpm and openmodeller-1.0.0-0.i386.rpm from this site:

_[Click here]("http://sourceforge.net/project/showfiles.php?group_id=101808&package_id=116659&release_id=684403")_

Save them on your desktop.
Then you need to install alien.```
sudo apt-get install alien
```

Now make .deb files from the rpms. ```
cd ~/Desktop
alien libopenmodeller-1.0.0-0.src.rpm
alien openmodeller-1.0.0-0.i386.rpm
```

Now install the debs.```
dpkg -i libopenmodeller-1.0.0-0.src.deb openmodeller-1.0.0-0.i386.deb
```

Post back if you run into any problems.

---

### Post by JFDS on 2009-06-23
Didn't work out

By the time I code alien libopenmodeller-1.0.0-0.src.rpm from the desktop directory this message is displayed:

Must run as root to convert to deb format (or you may use fakeroot)

Don't know what it means!:confused:

thanks

---

### Post by michy99 on 2009-06-23
Whenever you need to run a command as root, put 'sudo' in front of it.```
sudo alien libopenmodeller-1.0.0-0.src.rpm
sudo alien openmodeller-1.0.0-0.i386.rpm
sudo dpkg -i libopenmodeller-1.0.0-0.src.deb openmodeller-1.0.0-0.i386.deb
```
Sorry, I forgot about that.

---

### Post by JFDS on 2009-06-24
Hi michy

It worked fine! Altough I couldnt for some reason install the aplication using command lines, because when I transformed .rpm files to .deb using alien the resultant files in the desktop could not be modified for some reason, the permition to open them was denied. 

Then, I tried to open these files from the desktop with Gdebi pakcage and it installed finally the program.

I have found an OpenModeller Desktop version for Ubuntu Gusty and Hardy, but when I download and try to install them this message appears:

```
Error: La dependencia no se puede satisfacer: libgdal1-1.4.0 (sorry, my computer is set on spanish), but it will be something like "the libgdal1-1.4.0 dependency could not be satisfied"
```

Is there any way to install this version in Jaunty?

Thanks a lot for your help!

---

### Post by michy99 on 2009-06-24
The repository has libgdal1-1.5.0 I'm not sure if that will work, but you can try it.```
sudo apt-get install libgdal1-1.5.0
```

---

### Post by JFDS on 2009-06-24
I already installed the libgdal1-1.5.0 but is not woking!

I will keep trying other options

Thanks

---

### Post by michy99 on 2009-06-24
One other thing to try is download the hardy .deb for libgdal1-1.4.0 and install it manually:

[http://packages.ubuntu.com/hu/hardy/libgdal1-1.4.0](http://packages.ubuntu.com/hu/hardy/libgdal1-1.4.0)

---

