---
title: "Installing Tovid"
date: 2006-02-04
forum: Desktop Environments
---

### Post by TomAnthony on 2006-02-04
I am installing Tovid, and believe I have all the required dependicies. I can run the $ ./configure , but when i try to run $ su -c 'make install' it tells me
bash: make: command not found

Any idea why this is happening and what I can do to make this work?

---

### Post by taurus on 2006-02-04
By any change you haven't installed GCC and all the necessary files to compile a program!  Try

sudo apt-get install build-essential

---

### Post by TomAnthony on 2006-02-04
That worked, thanks. Now when i try to run su -c './setup.py install' for the gui, I get the error: error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

Any ideas here?

---

### Post by taurus on 2006-02-04
Sounds to me like you don't have python on your system!  Fire up sypnatic and install python from it!  If not sure, click on the Search field (upper right) and type in "python" for it...  Highlight whichever version you want to install and go for it.

---

### Post by TomAnthony on 2006-02-04
I did that, but there is a lot of python packeges available, a lot of which are already installed. Any idea which one to install for Ubuntu 5.10 that would allow me to finish this install?

---

### Post by taurus on 2006-02-04
Make sure you also install the development package(s) for python...  On the other hand, you can install tovid with apt-get!!!

---

### Post by TomAnthony on 2006-02-04
I have had good results using apt-get, but am not sure how to use it. How would I get tovid with apt-get?

---

### Post by taurus on 2006-02-04
sudo apt-get install tovid
-or-
sudo apt-get install <package name>
-or-
man apt-get

---

### Post by TomAnthony on 2006-02-04
Errror message: E: Couldn't find package tovid

---

### Post by taurus on 2006-02-04
Maybe because of your /etc/apt/source.lst!  What does it look like anyway?

---

### Post by TomAnthony on 2006-02-04
Here it is:

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by TomAnthony on 2006-02-04
Bump for any other ideas.

---

### Post by taurus on 2006-02-04
No need to bump!  I had to go into the office for a few hours...  Just add these three lines at the end of your /etc/apt/sources.list

# tovid:  Divx -> DVD...
deb [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free
deb-src [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free

Then, run

sudo apt-get update
sudo apt-get install tovid

---

### Post by rickwood on 2006-02-04
I installed tovid yesterday, and now have it working well.

The version in the kirya repository is not the most recent.  Although many people seem to be having success with that one, I had problems when trying to make a DVD.  So I uninstalled that version using Synaptic, and downloaded the most current version from here:

[http://download.berlios.de/tovid/tovid-0.24.tar.gz]("http://download.berlios.de/tovid/tovid-0.24.tar.gz")

I then followed the instructions for the source tarball found here, but substituted "sudo" for "su":

[http://tovid.berlios.de/en/install.html]("http://tovid.berlios.de/en/install.html")

A list of dependencies can be found here:

[http://tovid.berlios.de/en/dependencies.html]("http://tovid.berlios.de/en/dependencies.html")

I didn't bother checking these too close since I've got a bunch of related programs already installed.  However, I did notice that it indicates that wxPython 2.6 or newer is required.  When searching in Synaptic for wxPython, here's what I've got installed:  python2.4-opengl (2.0.1.09-1ubuntu4), python-opengl (2.0.1.09-1ubuntu4), python-wxgtk2.6 (2.6.1.1.1ubuntu2), python-wxtools (2.6.1.1.1ubuntu2), python-wxversion (2.6.1.1.1ubuntu2).

I've only burned one DVD so far (Frosty the Snowman and Rudolph the Red Nosed Reindeer), but it worked flawlessly.

Also note that in previous versions of tovid, you were required to install two packages -- tovid and tovid-gui.  In the most recent version (0.24), they are integrated together.  All you need is the zipped tarball in the first link above.

Hope this helps.

---

### Post by jtpratt on 2006-03-14
I had the exact same problem, and found the answer in another thread.  Simply run these 2 commands in terminal, and then install Tovid again and everything will work:

$ sudo apt-get install python-wxgtk2.4
$ sudo apt-get install python-dev

---

### Post by jpfinley on 2006-05-05
I am having all sorts of problems with tovid.

I cannot find tovid with apt-get, even when I have> 
# tovid: Divx -> DVD...
deb [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free
deb-src [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free
as part of my sources.list.

I downloaded the source tar.gz and this is what I get> 
john@aux:~/Desktop$ cd tovid-0.25.tar.gz
john@aux:~/Desktop$ tar -xzvf tovid-0.25.tar.gz
tovid-0.25/
tovid-0.25/src/
tovid-0.25/src/makevcd.sh
tovid-0.25/src/makexml.sh
tovid-0.25/src/pymakexml.py
tovid-0.25/src/tovid-init.sh
tovid-0.25/src/previd.sh
tovid-0.25/src/Makefile.am
tovid-0.25/src/Makefile.in
tovid-0.25/src/idvid.sh
tovid-0.25/src/tovid-interactive.sh
tovid-0.25/src/dvrequant.sh
tovid-0.25/src/tovid-init.sh.in
tovid-0.25/src/postproc.sh
tovid-0.25/src/pytovid.py
tovid-0.25/src/makeslides.sh
tovid-0.25/src/tovidgui.py
tovid-0.25/src/tovid-batch.sh
tovid-0.25/src/makemenu.sh
tovid-0.25/src/pymakemenu.py
tovid-0.25/src/tovid.sh
tovid-0.25/src/tovid-test.sh
tovid-0.25/src/makedvd.sh
tovid-0.25/NEWS
tovid-0.25/docs/
tovid-0.25/docs/man/
tovid-0.25/docs/man/makemenu.1
tovid-0.25/docs/man/makedvd.1
tovid-0.25/docs/man/makexml.1
tovid-0.25/docs/man/makeslides.1
tovid-0.25/docs/man/tovid.1
tovid-0.25/docs/man/idvid.1
tovid-0.25/docs/man/postproc.1
tovid-0.25/aclocal.m4
tovid-0.25/icons/
tovid-0.25/icons/tovid_icon_32.png
tovid-0.25/icons/tovid_icon_48.png
tovid-0.25/icons/tovid_icon_64.png
tovid-0.25/icons/tovid_icon_128.png
tovid-0.25/README
tovid-0.25/configure
tovid-0.25/configure.ac
tovid-0.25/install-sh
tovid-0.25/missing
tovid-0.25/Makefile.am
tovid-0.25/Makefile.in
tovid-0.25/setuplib.py.in
tovid-0.25/AUTHORS
tovid-0.25/setup.sh
tovid-0.25/INSTALL
tovid-0.25/libtovid/
tovid-0.25/libtovid/TDL.py
tovid-0.25/libtovid/Option.py
tovid-0.25/libtovid/Disc.py
tovid-0.25/libtovid/Globals.py
tovid-0.25/libtovid/Project.py
tovid-0.25/libtovid/Video.py
tovid-0.25/libtovid/Menu.py
tovid-0.25/libtovid/__init__.py
tovid-0.25/libtovid/VideoPlugins.py
tovid-0.25/libtovid/Standards.py
tovid-0.25/ChangeLog
tovid-0.25/COPYING
tovid-0.25/bootstrap
john@aux:~/Desktop$ cd tovid-0.25
john@aux:~/Desktop/tovid-0.25$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
configure: Checking for required core dependencies...
checking for grep... ok
checking for sed... ok
checking for md5sum... ok
checking for mplayer... ok
checking for mencoder... MISSING
checking for mplex... ok
checking for mpeg2enc... ok
checking for yuvfps... ok
checking for yuvdenoise... ok
checking for ppmtoy4m... ok
checking for mp2enc... ok
checking for ffmpeg... ok
checking for sox... ok
configure: Checking for optional dependencies...
configure: Checking for ImageMagick...
checking for composite... ok
checking for convert... ok
configure: Checking for dvd tools...
checking for spumux... ok
checking for dvdauthor... ok
checking for growisofs... ok
checking for mkisofs... ok
configure: Checking for vcd tools...
checking for vcdxbuild... ok
checking for cdrdao... ok
configure: Checking for transcode...
checking for tcprobe... ok
checking for tcrequant... ok
configure: error:

  Could not find these REQUIRED dependencies:

    mencoder   part of mplayer ([www.mplayerhq.hu](www.mplayerhq.hu))

  Please install the missing dependencies and ./configure again.
  Go to [http://tovid.org](http://tovid.org) for more help.

john@aux:~/Desktop/tovid-0.25$


The thing is, my mplayer installation is up to date according to apt-get.  Any ideas?

---

### Post by razorbuzz on 2006-05-13
>>  Could not find these REQUIRED dependencies:

>>  mencoder part of mplayer ([www.mplayerhq.hu](www.mplayerhq.hu))


Try doing a:
          apt-get install mencoder
Then try again.

---

### Post by tuxcantfly on 2006-06-25
[http://tovid.sourceforge.net/download/kubuntu/](http://tovid.sourceforge.net/download/kubuntu/)

has deb packages

---

### Post by troughton on 2006-08-05
i run tovid and todisc i got them off the websight for tovid and the irc channel is very helpfull on the webpage it lists the dependancys you need to make it work and if you get stuck go on the irc freenode and then /join #tovid the team that wrote it are ther and they are nice ppl and very helpfull

---

### Post by user1397 on 2006-08-23
if you want a nice little guide i have made that always works (or almost always) try this: [FONT=Verdana][SIZE=2][making dvd videos from avi files]("http://ubuntuforums.org/showthread.php?t=183936")[/SIZE][/FONT]

---

### Post by javedlodhi on 2008-02-12
> **TomAnthony said:**
> Errror message: E: Couldn't find package tovid
Specify the source to tovid in /etc/apt/source.lst file or you can specify that in SYSTEM > ADMINISTRATION > SOFTWARE SOURCES > THIRD-PARTY SOFTWARE and clicking the ADD button, just specify the source URL.

Otherwise you can follow this link:
[http://tovid.wikia.com/wiki/Main_Page#Get_tovid](http://tovid.wikia.com/wiki/Main_Page#Get_tovid)
and for dependencies
[http://tovid.wikia.com/wiki/Tovid_dependencies](http://tovid.wikia.com/wiki/Tovid_dependencies)
--
Regards,

Javed Lodhi
Expert Systems (Pvt) Ltd

---

