---
title: "amsn 0.97b + antialiasing in Feisty"
date: 2007-05-06
forum: Desktop Environments
---

### Post by marcozs on 2007-05-06
Hi all,

I spent the night googling around to find an amsn 0.97b compiled with antialiasing for Feisty. I couldn't get the debs anywhere here in the forum, so I will give you the links I found.

First install:
[TCL 8.5.0.a5]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/tcl8.5_8.5.0.a5-3v1ubuntu0_i386.deb")
[TK 8.5.0.a5]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/tk8.5_8.5.0.a5-3v1ubuntu0_i386.deb")
[Tile 0.7.8]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/tile_0.7.8-3v1ubuntu0_i386.deb")
[TCLTLS 1.5.0]("http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tcltls_1.5.0-3~neto1-3v1ubuntu0_i386.deb")

then the amsn package:
[aMSN 0.97b]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/amsn_0.97-0+svn20070426~3v1ubuntu1_i386.deb")

With a very nice skin (got it from amsn official website), it's gonna look like this:

---

### Post by bludhound on 2007-05-08
Just what I need.. Thanks!!

---

### Post by kaffelars on 2007-05-08
Great, looking forward to trying this out :)
I like aMSN, but it doesn't look too good without antialiasing.

---

### Post by larsemil on 2007-05-08
i love you. this was exactly what i needed.

---

### Post by JRaz on 2007-05-08
I'm guessing this is 32 bit and if so does anyone know where I could get the same packages but for 64 bit?

---

### Post by crapapelada on 2007-06-11
Hello,
I receive an error regarding dependencies when I try to install aMSN.
It says:
**Error: Dependency is not satisfiable: libc6**
libc6 is obviously installed.
What can I do?
Thanks!

---

### Post by patrickfromspain on 2007-06-11
Just compile it! It isn't hard....

sudo apt-get install libpng12-dev imagemagick libjpeg62-dev libxft dev

download from [www.tcl.tk](www.tcl.tk) tk8.5 and tcl8.5. Extract both and open a terminal

cd /path/to/tcl/folder/unix
./configure --prefix=/opt/tcltk
make
sudo make install

cd /path/to/tx/folder/unix
./configure --prefix=/opt/tcltk --enable-xft
make
sudo make install

Download amsn source from [www.amsn-project.net](www.amsn-project.net) and unpack it

cd /to/amsn/folder
./configure --prefix=/opt/amsn97 --with-tk=/opt/tcltk/lib --with-tcl=/opt/tcltk/lib
make
sudo make install

sudo touch /usr/local/bin/amsn
gksudo gedit /usr/local/bin/amsn and paste this:

#!/bin/bash

/opt/tcltk/bin/wish8.5 /opt/amsn/bin/amsn

save and close

sudo chmod +x /usr/local/bin/amsn

that's it!

---

### Post by crapapelada on 2007-06-11
Thanks, I'm a complete noob (in case it wasn't clear yet), so I'll try it.
:p

---

