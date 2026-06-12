---
title: "&quot;make&quot; as in &quot;make install&quot; &quot;make menuconfig"
date: 2006-03-02
forum: Desktop Environments
---

### Post by d0m1nation on 2006-03-02
after a fresh new install of ubuntu 5.10 i tryed to install a program from source.
unpacked the package, went in the dir, typed "make menuconfig" i told me i ddnt have "make" installed "make" tryed again and it worked but it showed alot of errors.
What is it more that i have to install to get the install to work? :-k 

thanx!

//d0m1nation

---

### Post by akiro.yamamoto on 2006-03-02
Please install build-essentials with Synaptic or use apt-get on the terminal.
This should get the packages you need from your install disk and install them 
on your system. 
Build essential includes the packages normally needed to create/build an app
from source. Check my sig for more info.

---

### Post by d0m1nation on 2006-03-02
Well, i tried to apt for it, but no luck, i just can´t find it :???:

---

### Post by carlosqueso on 2006-03-02
It's build-essential.  It SHOULD work then, but post back if you have problems.

---

### Post by bikeman on 2006-03-02
What command did you use in the terminal?  It should be:
sudo apt-get install build-essential

If you you get an error message that the package was not found, then you probably have to update your sources list.  This page will tell you how:
[http://ubuntuguide.squarecows.com/doku.php#repositories]("http://ubuntuguide.squarecows.com/doku.php#repositories")
Follow the instrucitons on how to add extra repositories and then use 
sudo apt-get update and then sudo apt-get upgrade.

Once you have build-essentials installed, make will work.  However, you may get a number of error messages indicating that there are other packages that need to be installed.  Simply make a list of these packages, and then install them using  sudo apt-get install *package-name*  replacing *package-name* with the real name from the error messages.  Once you have installed all of these dependencies, go back and use the make command for the program that you wanted to install.

---

### Post by d0m1nation on 2006-03-02
Okey, there is only one problem, i´ve put in alot of sources i really need, can you paste the thing i need so i don´t have to erase it all? :-D

---

