---
title: "How to install???"
date: 2009-04-23
forum: General Help
---

### Post by mubbashar on 2009-04-23
i download vlc .tar.bz2 file from net and i dont know how to install them the instruction in the install file are given below 

INSTALL file for the VLC media player

More extensive information for *nix, Windows, Mac OS X and BeOS users can be found here: 
[http://developers.videolan.org/vlc/](http://developers.videolan.org/vlc/)

Bootstrapping VLC
=================

If you retrieved VLC from the SVN server and do not have a "configure"
script, please refer to the HACKING file.

Configuring VLC
===============

A typical way to configure VLC is:

   ./configure --prefix=/usr

See `./configure --help' for more information.

If you intend to debug stuff, you may want to compile with debugging
symbols:

   make distclean ; ./configure --prefix=/usr --enable-debug

We recommend using GCC to build VLC, though some people reported success
with the Intel C compiler (version 8) as well. GCC version 3.3 or higher is
required. On older systems (e.g. FreeBSD 4.x, BeOS), please select a more
recent version manually by setting the CC and CXX environment variables
appropriately while running the ./configure shell script.


Building VLC
============

Once configured, run `make' to build VLC.


Installing and running VLC
==========================

You can install the VLC and its plugins by typing:

   make install

But you don't need to install it if you don't want to; VLC can be launched
from the current directory as well:

   ./vlc


Building packages
=================

To build a Debian package, you need to get the packaging info
   svn co svn://svn.debian.org/pkg-multimedia/videolan/vlc/debian debian 
and then
   dpkg-buildpackage -rfakeroot -us -uc


To build RedHat packages, use:

   rpm -ba vlc.spec

To build an ipkg package (iPAQ familiar Linux), use:

   ipkg-buildpackage



i dont understand this
please tell me how to install because i am new to ubunto........

---

### Post by RedSingularity on 2009-04-23
Get VLC from the package manager.  Much easier that way.  System>Admin>Package manager.  Search VLC.

---

### Post by mjitkop on 2009-04-23
+1 for the package manager.

The package manager that is built in Ubuntu is one of the reasons why Ubuntu is easy to use to install new applications. Feel free to use the package manager to install any application you want and try them, they're free!

---

### Post by mubbashar on 2009-04-23
it is correct but my net speed is very slow and i want to install it in this way.....if anybody help me

---

### Post by RedSingularity on 2009-04-23
Did you extract the folder from the .tar file yet?

---

### Post by mubbashar on 2009-04-23
yes

---

### Post by RedSingularity on 2009-04-23
Put the extracted folder in /usr/local/bin.

Then go to a terminal and type "cd /usr/local/bin/FOLDER NAME"

Once in there in terminal  type ./configure (If you get errors post them here)

If it finishes ok type 

1)make 
2)sudo make install

---

### Post by anjilslaire on 2009-04-23
open a terminal in the extracted folder that has a file called 'make' and in the terminal simply type
```

make

```
then
```
make install 
```

---

### Post by mubbashar on 2009-04-23
in folder  /usr/local/bin there is no option to paste folder ..

---

### Post by RedSingularity on 2009-04-23
You need root permission. 

Type "sudo nautilus" in terminal.

---

### Post by oldos2er on 2009-04-23
Vlc is a bear to compile. In addition to the file you downloaded, you would also need to download a multitude of dependencies.

 If you've got another machine you can download to, try Keryx: [http://keryx.betaserver.org/](http://keryx.betaserver.org/)
or [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by mubbashar on 2009-04-23
all things are ok but at the end it give me this error that

configure: WARNING: libhal >= 0.5.0 was not found. Install libhal-dev ?
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?

---

### Post by oldos2er on 2009-04-23
> **mubbashar said:**
> all things are ok but at the end it give me this error that

configure: WARNING: libhal >= 0.5.0 was not found. Install libhal-dev ?
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?

 As I said, there are many dependencies you'll need. libhal-dev and libdbus-dev are just the first two.

---

### Post by NS RAO on 2009-04-23
Hi, 
Thanks for information, I want new release Ubuntu CD`s , How to send request for Ubuntu CD`s.

Thanks 
Nadeem Saleem

---

### Post by mubbashar on 2009-04-23
from where i can install libhal-dev and libdbus-dev ??????????

---

### Post by oldos2er on 2009-04-23
From the repositories.

---

### Post by oldos2er on 2009-04-23
> **NS RAO said:**
> Hi, 
Thanks for information, I want new release Ubuntu CD`s , How to send request for Ubuntu CD`s.

Thanks 
Nadeem Saleem

 Please don't hijack threads.

 [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by mac9416 on 2009-04-24
oldos2er was right in pointing you toward Keryx. Get Keryx, make a "project" on your home computer, take it to your favorite hotspot on a flash drive (the library is a good one), then run it and tell it to download VLC (Keryx will automatically download all dependencies). Then, take the flash drive home and install the debs one by one. Installing debs this way is hard, but it's better than installing from source. In the next release of Keryx, it will have the ability to put the debs into a home-spun local repository, making software installation a lot easier.

keryxproject.org

---

### Post by jamessnell on 2009-04-24
Here's what I'd do.. (If I was insistent on not using the package manager for some resason)

1. Open a Terminal

2. Type in each of the following lines:
```

sudo su
mkdir /opt/vlc-src
mv vlc.tar.bz2 /opt/vlc-src
cd /opt/vlc-src/
tar -xzvf vlc.tar.bz2
ls

```

3. If the archive uncompressed in to /opt/vlc-src/<some directory>, then I'd run
```

mv <some directory>/* .
rmdir <some directory>

```

4. Then I'd build/compile vlc
```

./configure
make

```

5. Provided no fatal errors occured, I'd then link up the binary produced to somewhere in my path:
```

ln -s /opt/vlc-src/vlc /usr/bin/

```

IF a fatal error did occur, then I'd read the readme and figure it out: 
```

cat README

```


Hope that helps.

---

