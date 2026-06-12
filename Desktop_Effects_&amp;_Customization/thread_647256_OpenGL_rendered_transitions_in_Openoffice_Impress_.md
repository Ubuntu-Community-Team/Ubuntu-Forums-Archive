---
title: "OpenGL rendered transitions in Openoffice Impress Ubuntu Gutsy"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by avilella on 2007-12-22
Hi all,

I wanted to have transogl working with go-oo openoffice for Ubuntu Gutsy.

[http://wiki.services.openoffice.org/wiki/Impress:_OpenGL_rendered_transitions](http://wiki.services.openoffice.org/wiki/Impress:_OpenGL_rendered_transitions)
[http://rodo.foo.cz/blog/?p=31](http://rodo.foo.cz/blog/?p=31)

So I compiled it with these steps:

# building ooo-build on Ubuntu Gutsy:

sudo apt-get install libpam-dev libpng12-dev flex bison

sudo apt-get install libgtk2.0-dev

sudo apt-get install libcupsys2-dev 

sudo apt-get install sun-java6-jdk

sudo apt-get install gperf libjpeg-dev libxslt-dev libdb4.2-dev libpq-dev libcurl4-openssl-dev libodbc++-dev libiodbc2-dev

sudo apt-get install libldap2-dev libxul-dev libsane-dev libxaw7-dev libgnomevfs2-dev libgl1-mesa-dev

sudo apt-get install libglut-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev

sudo apt-get install libqt3-headers libqt3-mt-dev kdebase-dev

sudo apt-get install mono mono-devel

sudo cpan 

cpan> install Archive::Zip

###

svn checkout [http://svn.gnome.org/svn/ooo-build/trunk](http://svn.gnome.org/svn/ooo-build/trunk) ooo-build 

cd ooo-build

svn update

./autogen.sh --with-distro=UbuntuGutsy --with-tag=src680-m241 --disable-mono --disable-access --without-java --disable-kde --disable-dependency-tracking --disable-neon --enable-opengl

# also use " --with-num-cpus=2" if you have a dual core computer (or 4 for quad core), which speeds up the compilation
./download

# the lang package needs to be manually downloaded, as  the Debian (and therefore also 

# the Ubuntu) patchset contains a patch touching the localisation files

cd src && wget [http://download.go-oo.org/SRC680/src680-m241-lang.tar.bz2](http://download.go-oo.org/SRC680/src680-m241-lang.tar.bz2) && cd ..

# disable ubuntu-lpi patch

#  no Ubuntu guy updated their patches for recent milestones yet

perl -p -i -e 's/ubuntu-lpi/\#ubuntu-lpi/' patches/src680/apply

make
# This took 2-3 hours on my laptop, YMMV

bin/ooinstall ../m241

and then you can start using it.

Transogl effects are:

"Flipping tiles"
"Outside turning cube"
"Revolving circles"
"Turning helix"
"Inside turning cube"

Gstreamer is also integrated, so you can paste your videos as well.

---

### Post by Andrew.Z on 2008-02-17
There are actually ten transitions now, and here's [binary downloads and videos of the new OpenGL OpenOffice.org transitions](http://www.oooninja.com/2008/02/eye-candy-3d-opengl-transitions-impress.html).  The download is in RPM format, but it's easy to convert with alien.

---

### Post by josephmc on 2008-05-28
sudo apt-get install openoffice.org-ogltrans

just make sure you close all OO apps then re open after you install

---

### Post by avilella on 2008-05-31
> **josephmc said:**
> sudo apt-get install openoffice.org-ogltrans

just make sure you close all OO apps then re open after you install

I couldn't fint the package? Where is it?

 sudo apt-get install openoffice.org-ogltrans
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice.org-ogltrans

---

