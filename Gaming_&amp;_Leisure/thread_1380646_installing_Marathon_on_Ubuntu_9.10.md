---
title: "installing Marathon on Ubuntu 9.10?"
date: 2010-01-13
forum: Gaming &amp; Leisure
---

### Post by Qualia on 2010-01-13
I want to install aleph one one my machine so I can play Marathon Eternal, but when I download the folder for Aleph One, it gives me this "tar.bz2" 

what do I do with it? I cant seem to find any executables in it that would run the scenario I want to play.

How would I get around installing it? So far all of the walkthroughs I have seen have not been helpful..

I'm relatively new to linux, so pardon the noobishness... :D

if you want to look at the files yourself, here is the link:
[http://source.bungie.org/get/](http://source.bungie.org/get/)

---

### Post by llama320 on 2010-01-13
You need to unpack the tarball. Try this:
```
tar -jxvf filename.tar.bz2
```

---

### Post by Qualia on 2010-01-13
ok, I extracted the folder, using that method, and added the scenario files to the folder, but how do I run it?

Here is a screenshot of the folder:
[IMG]http://2332007279600767893-a-1802744773732722657-s-sites.googlegroups.com/site/slatesolid/home/other/Screenshot-1.png?attachauth=ANoY7cqPjH0_m0211PL0atUlBzmIHKs0zSIQIQF8U350qoOT85PWlG5xfJNP4H52f8auKbFjVQ5vuvGIttsi-clBpkHaNv8ePsFvwxCvicCYZg8HwUEw8NbjDr4589P1FSfmzeL2wAv6lXDT5twzu6ncAn1_uS9XsJlm2alNi6A2LdlV7wQ4J1aCEj2GvHyiuEANWivoifIBSvmIWajjkc-9pg71wXtX6Q%3D%3D&attredirects=0[/IMG]

---

### Post by llama320 on 2010-01-13
Try reading the INSTALL.Unix file. If you're using GNOME:
```
gedit INSTALL.Unix
```
Or if you're on KDE:
```
kate INSTALL.Unix
```
If that file isn't enlightening, try this page:
[http://gwos.org/doku.php/guides:32bit:alephone#alephone](http://gwos.org/doku.php/guides:32bit:alephone#alephone)

---

### Post by iamanidiot123 on 2011-07-24
Open a terminal, run ```
./configure && make
``` inside the directory.
If you get an error, run this (you need an internet connection:


```
sudo apt-get install libsdl1.2-dev libsdl-net1.2 libsdl-net1.2-dev zziplib-bin libzzip-dev libboost-dev libsndfile1 libsndfile1-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libmadlib-dev libsmpeg-dev libspeex-dev libspeexdsp-dev libmad0-dev g++ build-essential automake autoconf
```

Afterwards, if everything is successful, run ```
sudo make install
```

Place the scenerio files into /usr/local/share/AlephOne. you need to be the superuser (root) to do this. then, from the terminal, run ```
alephone
``` to start the game.

TUTORIAL TIME: sudo means run as superuser.  You need to be in the sudoers file.  More on that later.  You will be prompted for your password.
apt-get is your package manager, and the long list after that is the list of packages you are telling it to install.
./configure means execute the file 'configure'.
make is a compilation command.  ./configure runs a script to generate a Makefile, and make follows the commands in the Makefile.
'make install' runs target 'install' in your makefile.  Not all Makefiles has a target 'install'.  Installation must be run as root, as executables are to be put in your PATH to make them commands that are able to be run in your terminal.  

'&&' just means to run the second command after running the first command.  Without it the second command will be treated as an argument for the first command.


I hope I enlightened you tooday!

And now, the new home site of alephone is at marathon.sourceforge.net

---

