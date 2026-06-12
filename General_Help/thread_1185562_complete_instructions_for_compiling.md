---
title: "complete instructions for compiling"
date: 2009-06-12
forum: General Help
---

### Post by jeremyjjbrown on 2009-06-12
Hi,

Can anyone point me to a complete set of instructions for compiling from code, and tarballs. I am ready to start adding software to my machines from source but I haven't seen a complete primer.

Thanks!

---

### Post by colau on 2009-06-12
> **jeremyjjbrown said:**
> Hi,

Can anyone point me to a complete set of instructions for compiling from code, and tarballs. I am ready to start adding software to my machines from source but I haven't seen a complete primer.

Thanks!
```

tar vzxf filename.tar.gz
cd filename
./configure
make
sudo make install

```

---

### Post by michy99 on 2009-06-12
Read this:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by benj1 on 2009-06-12
> **colau said:**
> ```

tar vzxf filename.tar.gz
cd filename
./configure
make
sudo make install

```

thats generally the standard way, but read the README, that will have specific instructions for that particular package

---

### Post by colau on 2009-06-12
Yes,that's right.
It depends on the source code.
Reading the REDME file from the source code is better.

---

### Post by jeremyjjbrown on 2009-06-12
So check the readme or 

tar vzxf filename.tar.gz
cd filename
./configure
make
sudo make install

Man this Linux stuff is SO complicated ;)

Thanks!

---

### Post by eilios on 2009-06-12
I prefer using sudo su for compiling, no idea why(might just be a bad habit, I dunno). Assuming the file is helloworld.tar.gz;
```

tar vzxf helloworld.tar.gz
cd helloworld
sudo su
./configure
make
make install

```
It's longer, but for me it's better(no idea why, again).

---

### Post by bacardiandwatermelon on 2009-06-12
you will only need to run the make install as sudo... no need for sudo su

e.g.
```
sudo make install
```

---

### Post by blackxored on 2009-06-12
1. Read the code
2. Fulfill library dependencies (local or chrooted)
3. Configure if uses autoconf
4. Make (edit makefiles if necessary)
5. Sudo Make Install
6. Enjoy it.

It is pretty much the same, get info about those steps.

---

### Post by eilios on 2009-06-12
> **bacardiandwatermelon said:**
> you will only need to run the make install as sudo... no need for sudo su
 
e.g.
```
sudo make install
```
I know, I just got into a bad habit as the first 3 or four times I tried 'sudo make install' and it completely failed(and wasted a lot of time in the process), and then I tried 'sudo su' and ran make install and it worked perfectly, after that I always used sudo su for compilations.
 
Bad habit, I know, but it's hard to break. :x

---

