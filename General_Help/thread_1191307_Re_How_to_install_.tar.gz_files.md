---
title: "Re: How to install .tar.gz files"
date: 2009-06-18
forum: General Help
---

### Post by hagantic42 on 2009-06-18
Ok I have a major problem every time I enter 
hagantic@ubuntu:~/firefox$ ./configure
bash: ./configure: No such file or directory
I have no idea what I'm doing wrong. By the way I'm trying to install the mozilla 3.5 beta.

---

### Post by Amilo1718 on 2009-06-18
as far i can read you're running the terminal as $ and not as # ...
what command do you want to give?

---

### Post by aysiu on 2009-06-18
Firefox should already be installed.

But if you want the Mozilla version for some reason, this will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Anyone who has to ask this sort of question has no need to compile Firefox from source.

---

### Post by ~sHyLoCk~ on 2009-06-18
To compile from source first you will need:
```
sudo apt-get install build-essential
```

---

### Post by robert shearer on 2009-06-18
If you dont want to build there is a ppa here..
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Follow the instructions. (use the greyed button to select version) add the ppa,reload synaptic and then install Ffox 3.5.
Runs happily without upsetting your current Ffox. Just don't use both at one time.

This ppa gives a daily build so each day (or whenever you update ) there will be another build to download.

(run ```
apt-get autoclean
``` now and then to clear out the old packages or your apt-cache may fill fast.

---

