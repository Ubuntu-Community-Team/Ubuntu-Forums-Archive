---
title: "Source Questions"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Stambo00 on 2006-01-05
Iv'e been trying to figure this out by myself for a while now and would love the help.

Whenever I try to install anything from source either one of two problems occur:

I type in "./configure" and I'm replied with "bash: ./configure: No such file or directory"

Sometimes "./configure" works for some programs and I then type "make" but I'm replied with "make: *** No targets specified and no makefile found.  Stop."

Any help would be great.

---

### Post by az on 2006-01-05
It depends.

Let's say you just downloaded foo.tar.gz

In general, to compile it you would need to

untar it

tar xvzf foo.tar.gz

That will create, say, the foo-1.1 directory.  Enter it.

cd foo*

Look around for the README

ls

If there is a README, read it.   It will probably say that youneed some dependencies.  Let's say that foo requires the gtk libs and the foobar libs.  

apt-cache search foobar
apt-cache search gtk

install the relevant -dev packages.  Those are the developmental headers which you need to compile stuff against.  Ex libgtk2.0-dev

Also, install the build-essential package to bring in the compiler and toolchain

So, if the source has a config script, run it

./configure

(The slashdot means run the file in the current directory.  The current directory is not in your path per se)

If that works, make it

make

If that works, install it

sudo make install

(You can use checkinstall to help you keep track of such a package installed from source

sudo checkinstall

---

