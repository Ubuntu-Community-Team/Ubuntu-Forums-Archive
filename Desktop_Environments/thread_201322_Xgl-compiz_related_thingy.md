---
title: "Xgl-compiz related thingy"
date: 2006-06-21
forum: Desktop Environments
---

### Post by [L|eWiOn] on 2006-06-21
Package libdrm was not found in the pkg-config search path.
Perhaps you should add the directory containing `libdrm.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libdrm' found
mklib: Making Linux shared library:  libGL.so.1.2
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld gaf exit-status 1 terug
mklib: Installing libGL.so.1.2 libGL.so.1 libGL.so in ../../../lib
mv: kan stat niet toepassen op `libGL.so.1.2': Onbekend bestand of map
make[2]: *** [../../../lib/libGL.so] Fout 1
make[2]: Map '/home/lewion/cvs/Mesa/src/glx/x11' wordt verlaten
make[1]: *** [subdirs] Fout 1
make[1]: Map '/home/lewion/cvs/Mesa/src' wordt verlaten
make: *** [default] Fout 1
lewion@lewion-desktop:~/cvs/Mesa$     


This is the error i get... anything i can do ???? i used this [http://www.ubuntuforums.org/showthread.php?t=132406](http://www.ubuntuforums.org/showthread.php?t=132406)

and got stuck at compiling Mesa
Now we are gonna build Mesa: <--- that thingy, runt it and it gives me the error above.. help is much appreciated ... :(

---

### Post by [L|eWiOn] on 2006-06-25
anyone???

---

### Post by JoWilly on 2006-06-25
Why do you want to compile it from source ?

All the latest uptodate xgl/compiz/mesa/glitz/gset-compiz,... packages are in the compiz repo:
[_http://www.compiz.info_]("http://www.compiz.info")

Edit: the reason it breaks is that you probably are missing the libdrm includes. You need to install the devel packages.

---

### Post by chadwick359 on 2006-06-27
Yeah, I'm a bit confused on why you would want to compile it too. I would suggest a vanilla install, avoid all that messy compiling. Complete dapper HowTo is linked in my signature. (gonna be updated in the next day or two, hopefully i can get some more speed increase.)

---

