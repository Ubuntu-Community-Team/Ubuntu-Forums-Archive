---
title: "tar,gz"
date: 2009-02-24
forum: General Help
---

### Post by baldydash on 2009-02-24
tried to install a tar.gz file no luck very new to ubuntu can anyone help

---

### Post by taurus on 2009-02-24
You need to be in the directory where you have saved that filename.tar.gz.  Then, unpack/uncompress with

```
tar xvzf filename.tar.gz
```
That would probably create a new directory so you need to change to that new directory and have a look at either readme.txt or INSTALL.

What are you trying to build/install and where did you download it?  If I know more the file/program, I can assist you more.

---

### Post by SoCalChris on 2009-02-24
Also, a .tar.gz file is just a compressed file. Think of it like a zip or rar file if you're coming from Windows.

---

### Post by baldydash on 2009-02-24
I downloaded total video converter and have tried what you suggested before this but no joy

---

### Post by taurus on 2009-02-24
What is the name of that program and where did you download it?  Are you trying to convert a video from one format to another?

---

### Post by baldydash on 2009-02-24
it's called total video converter i downloaded from their website I was hoping to change an avi file into dvd files

---

### Post by taurus on 2009-02-24
Devede is what you need.  It is available from the repos so install it either from add/remove, synaptic, or apt-get.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install devede
```
It should now be in Applications -> Sound & Video.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by linuxisevolution on 2009-02-24
Yes devede is the best for this kind of thing.

Click Applications >> Accessories >> Terminal and type in the box:

sudo apt-get install devede

and follow the instructions.

---

### Post by baldydash on 2009-02-24
got it looks like it will do the trick will have a bash tomorrow thanks for that

---

