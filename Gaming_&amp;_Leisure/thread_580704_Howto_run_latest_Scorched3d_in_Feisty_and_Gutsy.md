---
title: "Howto run latest Scorched3d in Feisty and Gutsy"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by ruibernardo on 2007-10-19
A few days ago a new version of Scorched3d came out.

The scorched3d version on the repositories in Feisty and Gutsy (version 40.1d) doesn't work no more with the official scorched3d servers (version 41). I've tried to install the RPM from their site (with alien) but I just got a "core dumped" error message, so I've compiled the game from sources.

So here it goes. Install the following packages (taken from my Synaptic history):

```
sudo apt-get install checkinstall autoconf automake1.7 autotools-dev m4 reeglut3-dev ghc6 ghc6-prof haskell-utils libghc6-glut-dev libghc6-opengl-dev libgl1-mesa-dev libglu1-mesa-dev libgmp3-dev libgmp3c2 libgmpxx4 libice-dev libncurses5-dev libreadline5-dev libsm-dev libx11-dev libxau-dev libxdmcp-dev libxext-dev libxt-dev mesa-common-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev  x11proto-xext-dev xlibmesa-gl-dev xtrans-dev libopenal-dev libalut-dev libogg-dev libopenalpp-cvs-dev libopenalpp-cvs1 libopenthreads-dev libopenthreads4 libvorbis-dev libghc6-openal-dev libfreetype6-dev zlib1g-dev fftw3 fftw3-dev libjpeg62-dev libpng12-dev libsdl-image1.2-dev libsdl1.2-dev libtiff4-dev libtiffxx0c2 libsdl-net1.2-dev mesa-swx11-source libglib1.2 libgtk1.2 libgtk1.2-common libwxbase2.4-1 libwxbase2.4-dev libwxgtk2.4-1 libwxgtk2.4-1-contrib libwxgtk2.4-contrib-dev libwxgtk2.4-dev wx2.4-headers libalut-dev libalut0

```**Only in Feisty:**
In Feisty I couldn't compile it with the freealut packages (libalut0 and libalut-dev) in the repository because they don't have a file (freealut-config). So you have to install them from the gutsy repository. To do it, open your sources.list in gedit and replace all "feisty" words to "gutsy" (please be careful to not upgrade your system while gutsy repos are on).

```
cp /etc/apt/sources.list /etc/apt/sources.list.temp
gksudo gedit /etc/apt/sources.list
```Then update the repositories and upgrade the following packages:

```
# PLEASE DO NOT UPGRADE, JUST UPDATE
sudo apt-get update
sudo apt-get install libalut-dev libalut0
# Put back your original sources.list
mv /etc/apt/sources.list.temp /etc/apt/sources.list
# update the repos back to Feisty
sudo apt-get update

```**[SIZE=3][COLOR=black]Compilation[/COLOR][/SIZE]**
Now that all is ready, compile scorched3d. Download the sources from [http://www.scorched3d.co.uk/downloadssrc.php](http://www.scorched3d.co.uk/downloadssrc.php) and extract it.Go to the directory were you extracted the source file and type:

```
chmod +x autogen.sh
./autogen.sh
make
sudo checkinstall
```Set the new version of scorched3d in the deb package by editing the version field (press 3 and type 41). Checkinstall will create the new deb package.

Install the new package with:

```
sudo dpkg -i scorched3d_41.0-1_i386.deb
```To play the game:

```
 /usr/local/games/scorched3d/bin/scorched3d
```Have a nice open source game.

---

### Post by derekr44 on 2007-10-19
Thank you very much for this.  I need my fix of nuking mayhem.

---

### Post by diegomedaglia on 2007-11-15
Hi!
   I downloaded the packages as you have instructed, except for "reeglut3-dev" which I imagine was "freeglut3-dev" and "libgmpxx4", which did not exist. I installed "libgmpxx4ldbl" instead, which was the closest match I could find.
   Then I ran the autogen.sh script, It worked until it tested the SDL installation. Here are the messages:

checking for SDL - version >= 1.2.5... no
*** Could not run SDL test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means SDL was incorrectly installed
*** or that you have moved SDL since it was installed. In the latter case, you
*** may want to edit the sdl-config script: /usr/bin/sdl-config
configure: error: *** SDL version 1.2.5 not found. Try [http://www.libsdl.org/](http://www.libsdl.org/)

I tried to modify line 5 of autogen.sh as follows:
./configure $* --disable-sdltest

It did run to the end without errors, but then 'make' generated the following error:

/usr/bin/ld: warning: libvga.so.1, needed by /usr/local/lib/libSDL.so, not found (try using -rpath or -rpath-link)
/usr/local/lib/libSDL.so: undefined reference to `vga_setpalette'
/usr/local/lib/libSDL.so: undefined reference to `keyboard_init_return_fd'
/usr/local/lib/libSDL.so: undefined reference to `vga_hasmode'
/usr/local/lib/libSDL.so: undefined reference to `vga_getcurrentmode'
/usr/local/lib/libSDL.so: undefined reference to `vga_init'
/usr/local/lib/libSDL.so: undefined reference to `keyboard_update'
/usr/local/lib/libSDL.so: undefined reference to `keyboard_seteventhandler'
/usr/local/lib/libSDL.so: undefined reference to `vga_waitretrace'
/usr/local/lib/libSDL.so: undefined reference to `vga_setlinearaddressing'
/usr/local/lib/libSDL.so: undefined reference to `vga_getmodeinfo'
/usr/local/lib/libSDL.so: undefined reference to `vga_lastmodenumber'
/usr/local/lib/libSDL.so: undefined reference to `vga_setpage'
/usr/local/lib/libSDL.so: undefined reference to `vga_setdisplaystart'
/usr/local/lib/libSDL.so: undefined reference to `mouse_seteventhandler'
/usr/local/lib/libSDL.so: undefined reference to `vga_setmode'
/usr/local/lib/libSDL.so: undefined reference to `vga_disabledriverreport'
/usr/local/lib/libSDL.so: undefined reference to `vga_setmousesupport'
/usr/local/lib/libSDL.so: undefined reference to `vga_getgraphmem'
/usr/local/lib/libSDL.so: undefined reference to `keyboard_close'
/usr/local/lib/libSDL.so: undefined reference to `mouse_update'
collect2: ld returned 1 exit status


I have SDL version 1.2.11 installed. Is there any way I can install version 1.2.5 simultaneously? Or is there a way to force scorched to compile against the newer version? I'm not familiar at all at with development for linux, so I imagine I'm just missing a symbolic link or something of the kind =P 

Thanks for helping!!

---

### Post by ruibernardo on 2007-11-15
> **diegomedaglia said:**
> Hi!
   I downloaded the packages as you have instructed, except for "reeglut3-dev" which I imagine was "freeglut3-dev" and "libgmpxx4", which did not exist.
You are right about "freeglut3-dev". About "libgmpxx4", I have it here on my repositories but when I search for it in [http://packages.ubuntu.com](http://packages.ubuntu.com), I only found this: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libgmpxx4](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libgmpxx4).

> **diegomedaglia said:**
> I installed "libgmpxx4ldbl" instead, which was the closest match I could find.Yes, I've upgraded to Gutsy now, and I can find it here too, so it must be a substitute for libgmpxx4 in Gutsy. 

> **diegomedaglia said:**
> Then I ran the autogen.sh script, It worked until it tested the SDL installation. Here are the messages:

checking for SDL - version >= 1.2.5... no
*** Could not run SDL test program, checking why...
*** The test program failed to compile or link. See the file [COLOR=Red]**config.log**[/COLOR] for the
*** exact error that occured. This usually means SDL was incorrectly installed
*** or that you have moved SDL since it was installed. In the latter case, you
*** may want to edit the sdl-config script: /usr/bin/sdl-config
configure: error: *** SDL version 1.2.5 not found. Try [http://www.libsdl.org/](http://www.libsdl.org/)

I think this is about a script that should be in a package, and I think that's the package I say to install from the Gutsy repositories (can't be sure). Maybe I missed a package in the list. Maybe the config.log file could help.  Can you post the config.log file?

---

### Post by diegomedaglia on 2007-11-16
Hi,
   I realized I had messed up with the /usr/local/lib/libSDL.so link when installing DOSBOX. I pointed it to /usr/lib/libSDL-1.2.so.0.11.0 and then compilation went OK (after I suppressed SDL testing in autogen.sh). After that I could not run scorched3D, it complained about libvga or something like that. The package did not exist, so I installed **libsvga1** and it is now running ok. 

Thanks for helping, once again!:)

---

### Post by SomeYahoo on 2007-11-16
This is my first compiling... and it worked!  Had to make some of the changes mentioned, and get essentials, etc... but I managed to get it to work.

Thanks for the help... invaluable to a noob like me.

P.S. for other noobs, be sure to un-install the old version first... duh!

---

### Post by saygin on 2007-11-20
Thanks a lot! However, I have some issues.
First, the deb file is created but when I install it, it doesn't create a shortcut on the menu and also there is no copy or link to the executable file in the /usr/bin/ . How can I make the deb file to do these? I created a script that runs the executable and I'm gonna copy it to /usr/bin/ but, it would be better if the package does it itself. Waiting for answers. Thanks!

---

### Post by ruibernardo on 2007-11-20
> **saygin said:**
> Thanks a lot! However, I have some issues.
First, the deb file is created but when I install it, it doesn't create a shortcut on the menu
You are compiling from sources and the sources don't have a menu item. To create a menu, right-click on the "Applications" menu and select "edit menu". Then add a menu item.
> **saygin said:**
> and also there is no copy or link to the executable file in the /usr/bin/ .
The executable is located at /usr/local/games/scorched3d/bin/scorched3d, so link it to /usr/bin/ if that's what you want - it's not the standard, as it is a compiled application, so it should be in /usr/local/. In linux, you are free to do what you want.
> **saygin said:**
> How can I make the deb file to do these? I created a script that runs the executable and I'm gonna copy it to /usr/bin/ but, it would be better if the package does it itself. Waiting for answers. Thanks!
checkinstall just runs like "make install" and creates a deb package of the installation. To do what you want you need to check the files created during the compilation and change one of them (Makefile?) so the script and links are included in the install process.

Please note that you can't install this package in another computer without installing all the dependencies. Without checkinstall you would need to keep the directory where you compiled the program to be able to remove it later. checkinstall makes removal easier. It isn't to create a deb package that you can use to install a program in another computer because it doesn't keep track of its dependencies (which you would need to install that deb package).

I hope this helps.

---

### Post by henriquemaia on 2008-01-03
Obrigado!!

Thanks a lot. I was trying to get the latest version installed without success and then I came across your post. 

Scorched 3d rocks.

---

### Post by Ozor Mox on 2008-01-24
Thanks for your useful instructions. I could not compile Scorched 3D until I installed all those packages, and now it is compiling fine. But how do you know which packages to install?

---

### Post by Perfect Storm on 2008-01-24
You know which one when the ./configure output are rolling by - also depending which options you will enable/disable

---

