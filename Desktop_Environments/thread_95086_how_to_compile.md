---
title: "how to compile"
date: 2005-11-25
forum: Desktop Environments
---

### Post by definity on 2005-11-25
hi, im new to ubuntu and linux

i just downloaded some programs and i had to compile them and i ahve no idear how to do it i did try to google it but didnt come up with anything usefull. Aswell one of the programs was airsnort i followed the instructions on there site but it did not work for me.
thanks in advanced

---

### Post by teaker1s on 2005-11-25
airsnort is in repositories
sudo synaptic in konsole search for it click and install
at the same time you want to install build-essential with synaptic

then you can cd into the source directory and then
 ./configure
make
install

---

### Post by kabus on 2005-11-25
To compile a program you should first install some necessary tools :

```
sudo apt-get install build-essential
```

then unpack the source tarball you downloaded :
```

tar -xzf  example.tar.gz
```

Next cd into the newly created directory *example*.
Look for a file named README or INSTALL and open it in a text editor. It will contain instructions, info on dependencies, etc.

Most likely you will just have to enter these commands to compile, though :

```
./configure
make
sudo make install
```

If you get any error messages you are probably missing some dependencies, so read the errors carefully and try to figure out what you need to install.

Good luck !

---

### Post by matthewv on 2005-11-25
On Ubuntu it is best to replace the last step (sudo make install) with a ```
sudo checkinstall
```Checkinstall must be installed first, but running this command will generate a .deb file and install that, so the program can later be installed and uninstalled using dpkg/apt-get/synaptic

---

### Post by erik-the-red on 2005-11-25
Be warned that most users on this board take advantage of the generally excellent Ubuntu repositories instead of compiling from source.

At least, that's what happened to me. I don't think Enlightenment DR16.7 and Thunderbird 1.0.7 are that obscure, but I'm still stuck as to what the name of the package is that I need for the former and why the latter won't run.

---

### Post by aysiu on 2005-11-25
[QUOTE=definity]Aswell one of the programs was airsnort i followed the instructions on there site but it did not work for me.[/QUOTE] Forget about the downloaded file. See the first link in my sig. Then open up a terminal and type ```
sudo apt-get update
sudo apt-get install airsnort
```

---

