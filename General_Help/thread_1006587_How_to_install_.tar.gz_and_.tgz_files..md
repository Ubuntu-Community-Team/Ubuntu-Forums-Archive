---
title: "How to install .tar.gz and .tgz files."
date: 2008-12-09
forum: General Help
---

### Post by sam1993 on 2008-12-09
I am trying to install Cowpatty, Airsnort and Kisment. But as I don't know how to install .tar.gz and .tgz files. I found Kismet on Synaptic Package Manager but it didn't install the part that allows me to use the program.

So could someone tell me how to install these files.

---

### Post by taurus on 2008-12-09
With .tar.gz (or .tar.bz2), you first need to be in the same directory where the file is.  Then, you need to uncompress and unpack it with the tar command.  That would create a new directory and you need to change to that new directory.  Now, there should be a INSTALL that tells you exactly what you need to do but most of the time, you need to compile the source for your machine.

```
cd ~/Desktop
tar xvzf filename.tar.gz
cd filename
sudo apt-get update
sudo apt-get install build-essential checkinstall
./configure
make 
sudo checkinstall
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by sam1993 on 2008-12-09
> **taurus said:**
> With .tar.gz (or .tar.bz2), you first need to be in the same directory where the file is.  Then, you need to uncompress and unpack it with the tar command.  That would create a new directory and you need to change to that new directory.  Now, there should be a INSTALL that tells you exactly what you need to do but most of the time, you need to compile the source for your machine.

```
cd ~/Desktop
tar xvzf filename.tar.gz
cd filename
sudo apt-get update
sudo apt-get install build-essential checkinstall
./configure
make 
sudo checkinstall
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)


Thank you. Good job you posted that link, because those commands you included lost me lol.

---

