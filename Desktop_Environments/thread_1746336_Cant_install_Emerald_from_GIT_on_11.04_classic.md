---
title: "Cant install Emerald from GIT on 11.04 classic"
date: 2011-05-01
forum: Desktop Environments
---

### Post by ShatPank on 2011-05-01
Yes, I'm back with more problems.

Basically, I installed compiz fusion Icon and Emerald so I could add a bit of eye candy.
Found out that apparently the latest version of compiz is not properly compatible with emerald, but apparently GIT has it fixed.

So I followed the instructions on this site [http://demonic.cc/?p=50](http://demonic.cc/?p=50)

However, when I get to ./autogen.sh I end up with the following.

Box:~/emerald$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:16: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:16: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: running: /usr/bin/autoconf
configure.ac:16: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1



Any help would be awesome.
Stu

---

### Post by beew on 2011-05-01
Hi,

I installed emerald in 11.04 sucessfully  with some help.
[http://ubuntuforums.org/showthread.php?t=1702253](http://ubuntuforums.org/showthread.php?t=1702253)

Can't help you with the fusion-icon though but it is actually quite unnecessary IMO.

---

### Post by steinerd on 2011-05-01
Follow this [http://deep-sea.realservers.info/ubuntu/enable-emerald-themes/](http://deep-sea.realservers.info/ubuntu/enable-emerald-themes/) I can't remember where i got all the info but it worked great for me.  Very easily done.:popcorn:

---

### Post by tnt533 on 2011-05-04
The key ingredients missing on the demonic.cc tutorial are making sure that the dependencies are installed;

sudo apt-get build-dep emerald

and that you use elevated permissions when you run "make install" with

sudo make install

instead of just make install without "sudo".

After I made those changes, Emerald went in perfectly fine without any patches and works like a champ.

Using the suggestions above, the demonic.cc tutorial is a little simpler way to get it up and running. I've included the whole thing below with the changes. I didn't write this, I only added the two things listed above to make it work.

If git is not installed or you are not sure then go ahead and run the following command then proceed with the rest below.

sudo apt-get install git curl


sudo apt-get -y install libtool build-essential intltool libdecoration0-desv
sudo apt-get build-dep emerald 
cd ~
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald
git checkout -b compiz++ origin/compiz++
./autogen.sh
make
sudo make install
cd ~
rm -rf emerald

after everything went through type the following command to enable emerald;

emerald --replace

---

### Post by lorebett on 2011-05-18
Hi

I'm using KDE (I upgraded to Natty)

I successfully built emerald from sources, and installed it (default to /usr/local/bin).

However, emerald --replace does not show any output, and enabling compiz as the window manager seems to work, but the KDE plasma desktop does not respond correctly in many situations...

---

