---
title: "linux headers PLease Help!"
date: 2005-05-28
forum: Desktop Environments
---

### Post by luvdemheels on 2005-05-28
I am getting the following try to install alsa:

"checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
"

I have extracted linux-source-2.6.10.tar.bz2 in /usr/src and everything is there. I even did a ln -s linux-source-2.6.10 linux in the /usr/src directory and still get the above.

Please help! Why is the file version.h missing from /usr/src/linux/include/linux???

The directory is there and has many other files.

---

### Post by luvdemheels on 2005-05-28
I'm past this now. I finally installed the correct headers though synaptic.

I was able to install alsa 1.09rc4 with no visable errors, ran alsaconf with no errors and rebooted.

Now my ubuntu Completely LOCKS up whenever I do anything with sound.  :-x 

I can't do anything but power off. Looks like alsa 1.09 will not work for me and I will have to reload my system from scratch.

---

### Post by sapo on 2005-05-28
Do you know what **APT-GET** is?

If you dont, i recommend you READ about it before your system will be in a so big mess... that you will have to reinstall it...

installing tar.gz and compiling from source in ubuntu is nuts.. of course if its some kind of newer version or if YOU KNOW EXACTLY what you are doing...  ](*,) 

try "man apt-get"

i dont know if there is a ubuntu apt-get page of something like it btw

[http://www.debian.org/doc/manuals/apt-howto/ch1.en.html](http://www.debian.org/doc/manuals/apt-howto/ch1.en.html)

And try typing "synaptic" in a graphical terminal...  :roll:

---

### Post by bored2k on 2005-05-29
[QUOTE=sapo]Do you know what **APT-GET** is? (...)[/QUOTE]
[QUOTE=Ubuntu Code of Conduct]
Be considerate
Be respectful.
Be collaborative.[/QUOTE]

To basically offend someone by pointing out stuff he/she is -according to you- supposed to know is not an accepted conduct here. Each one of us has the right to ask as much help as we need. And just so you know, there are countless Linux variants, and not all of them use apt-get as their main package management system.

Installing and compiling a source package in Ubuntu is not "nuts". If done correctly, it will work. It's harder than apt-get, but they still do the same thing.

To luvdemheels: on your upper panel click on System > Administration  > Synaptic and search for linux-headers. After you find what you desire, right click  > install.

P.S. - And remember:
[QUOTE=Ubuntu Code of Conduct]
When you are unsure, ask for help.[/QUOTE]

---

