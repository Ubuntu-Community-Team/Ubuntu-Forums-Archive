---
title: "Linux + PSP"
date: 2006-10-08
forum: Gaming &amp; Leisure
---

### Post by Siima on 2006-10-08
I'd like to know how's linux responding if connecting psp to it? And if using 
wlan through USB does it work? and are there software to make it work etc ..

Also is there any programms which can convert your video files into psp form for linux?

thx for help!

---

### Post by Kateikyoushi on 2006-10-09
There is a PSP manager for linux, [LINK]("http://sourceforge.net/projects/qpspmanager/").

Linux PSP Video converter also exists [LINK.]("http://sourceforge.net/projects/pspvc/")

Unfortunately there aren't as many as under windows.

---

### Post by s_h_a_d_o_w_s on 2006-10-12
I'm having a real hard time instlal those apps. Could youtell me how to install the tar.gz plaes? Thanks alot.

---

### Post by darkteckno on 2006-10-19
bumpety bunmp

---

### Post by s_h_a_d_o_w_s on 2006-10-20
Thanks for the bump. Ima bump it too and pm[URL="http://www.ubuntuforums.org/member.php?u=167218"] Kateikyoushi if none  replies soon. :-)
[/URL]

---

### Post by jb2kred on 2006-11-07
open console
tar -xvf pspvc-install-0.2.1.tar
cd /pspvc-install-0.2.1
sudo sh install
enter password

it then should install
run by typing
pspvc

---

### Post by mike998 on 2006-11-07
You will have to install some libraries for PSPVC to work.
If you go through synaptic and search for the libraries mentioned [here]("http://pspvc.sourceforge.net/") then you should be good to go.  You will also have to run the program from command line.  Occasionally it will simply create a thumbnail - I have no idea why and not all video files will work - it depends on the codec used by the original video.

EDIT : The libraries you will need are : libgtk2.0-dev, libfaac-dev, libxvidcore4-dev, nasm as well as build essential...

Don't worry too much about connecting.  The PSP will appear as a drive on your desktop.  Once you have transferred any and all files, make sure you UNMOUNT the PSP - don't disconnect the PSP unless it is completely dismounted or the file will not write to the PSP correctly.

By the way, I am very happy with the way that the PSP works with Ubuntu :-)

---

### Post by livinginx on 2006-11-09
Just for future reference:
a .tar.gz file or a .tar file are just archives or compressed files.  Similar to .rar, .zip, etc.

---

### Post by mike998 on 2006-11-10
Is it worthwhile me writing up the above posts and creating a how-to on installing pspvc?

---

### Post by s_h_a_d_o_w_s on 2006-11-11
Thanks but do u know how to install qpspmanager? I untar it but can't find the install.sh ? REally appreciate the reply.

---

### Post by darkteckno on 2006-11-18
anyone know?

---

### Post by cantormath on 2006-11-18
[I like the GP2X]("http://www.gp2x.com/")
Check it out.
[IMG]http://gp2x.co.uk/newblack.gif[/IMG]

---

### Post by nuclearj on 2006-11-18
> **s_h_a_d_o_w_s said:**
> Thanks but do u know how to install qpspmanager? I untar it but can't find the install.sh ? REally appreciate the reply.

I would like to find out too, QPSPManager looks like a strong application for this purpose.

---

### Post by nuclearj on 2006-11-18
So here's what I did

```
$ qmake qpspmanager.pro

```

and then

```
$ make Makefile
make: `Makefile' is up to date.

```

But then i got that error msg, so you may be able to skip that step, then

```
$ sudo make install

```

When its done you get a folder called "bin", go in there and double click the qpspmanager icon and it should start. :)

---

### Post by darkteckno on 2006-11-22
there is a Deb at this link now: [http://sourceforge.net/projects/qpspmanager/](http://sourceforge.net/projects/qpspmanager/)

---

### Post by manny0 on 2006-12-14
> **jb2kred said:**
> open console
tar -xvf pspvc-install-0.2.1.tar
cd /pspvc-install-0.2.1
sudo sh install
enter password

it then should install
run by typing
pspvc

i must be missing a package. i just installed ubuntu. and when i went to set up this program i did the command "sudo sh install" and i got "cannot execute binary file" please help i want to try this program out.

---

### Post by billyfoxtrot on 2006-12-14
> **manny0 said:**
> i must be missing a package. i just installed ubuntu. and when i went to set up this program i did the command "sudo sh install" and i got "cannot execute binary file" please help i want to try this program out.

I'm not sure exactly what's going wrong for you, but for me, I had to change line 56 in the install.sh file from

```
--extra-ldflags=-L$INSTALLDIR/share/pspvc/lib
```

to

```
--extra-ldflags="-L$INSTALLDIR/share/pspvc/lib -lX11"
```

---

### Post by ronybeck on 2007-01-03
> **billyfoxtrot said:**
> I'm not sure exactly what's going wrong for you, but for me, I had to change line 56 in the install.sh file from

```
--extra-ldflags=-L$INSTALLDIR/share/pspvc/lib
```

to

```
--extra-ldflags="-L$INSTALLDIR/share/pspvc/lib -lX11"
```



That didn't do it for me.  I had to change that line to add: --extra-libs="-lX11 -lx264" so that it now reads:

./configure --enable-faac --enable-x264 --enable-gpl --enable-xvid --enable-pthreads --prefix=$INSTALLDIR/share/pspvc --disable-debug --extra-cflags=-I$INSTALLDIR/share/pspvc/include --extra-ldflags=-L$INSTALLDIR/share/pspvc/lib --extra-libs="-lX11 -lx264"

And it installs just fine now.  In addition to this, I already had x264 and libx264-dev installed via synaptic.

---

### Post by manny0 on 2007-01-07
> **mike998 said:**
> Is it worthwhile me writing up the above posts and creating a how-to on installing pspvc?
completely worth it. i have no clue on how to get it on my computer. :(

---

### Post by hafestos on 2007-01-24
You can run 'make' now.
./install.sh: line 30: make: command not found
ERROR during compilation or installation of X264

i get that when i run ./install.sh

any help on how to make make work...

---

### Post by hafestos on 2007-01-24
ok, now i got make to work, but i get this error

make: *** [install] Error 1
ERROR during compilation or installation of X264

tried to install x264 and didnt change anything...

---

### Post by lamalex on 2007-04-15
have you tried the .deb file yet?

---

### Post by leszek44444 on 2007-06-04
Hello,

There is now documentation about PSP on the Ubuntu Wiki:
[https://help.ubuntu.com/community/PSP]("https://help.ubuntu.com/community/PSP")

---

### Post by soujiro14 on 2007-10-26
I did it exactly as shown, no beans.  Everything works up until where i have to compile the source.  Once I use "qmake", all I get is errors:

```

user@computer:~/downloads/qpspmanager-2.0.2$ qmake
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS

```

---

### Post by chacham23 on 2007-10-26
> **soujiro14 said:**
> I did it exactly as shown, no beans.  Everything works up until where i have to compile the source.  Once I use "qmake", all I get is errors:

```

user@computer:~/downloads/qpspmanager-2.0.2$ qmake
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS

```

happen to me also someone?

---

### Post by edward4130 on 2007-11-02
This just does not work. The current build is 2.0.2 and there is not a .sh to install, the code provided is not enough.

If anyone got this to work another way please provide something, I'm sure I'm not the only one that is hanging for the solution.

Edward4130

---

### Post by Hork on 2007-11-22
> **edward4130 said:**
> This just does not work. The current build is 2.0.2 and there is not a .sh to install, the code provided is not enough.

If anyone got this to work another way please provide something, I'm sure I'm not the only one that is hanging for the solution.

Edward4130

Yulp, I also need some help :(

---

### Post by funkyFlash on 2007-11-25
Ah.  Just figured it out and answered in [a smaller thread.]("http://ubuntuforums.org/showthread.php?t=569573")

Hope that helps.  Still haven't gotten around to editing the wiki.

On similar news, I can't get PSPVC to convert from a DVD source.  I've tried several ways of merging the VOB files into one huge VOB, and pspvc proudly responds with "source file not exists".  I don't want to encode them into something just so I can transcode them again...

---

### Post by funkyFlash on 2007-11-25
[This thread]("http://sourceforge.net/forum/forum.php?thread_id=1684676&forum_id=535914") shed some light on the subject.  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64, of course!  Why didn't I think of that?!  Lol.

I recompiled as described, and it worked.

---

### Post by Itaku on 2007-12-29
[This]("http://ubuntuforums.org/showthread.php?t=569573") fixed the whole problem for me and now it works.

---

### Post by preetyforu on 2008-01-23
If you are new to programming, then learn the language first on a PC platform before moving to other hardware otherwise you are on a VERY steep and slippery learning curve.

---

### Post by rp3 on 2008-01-26
> **hafestos said:**
> ok, now i got make to work, but i get this error

make: *** [install] Error 1
ERROR during compilation or installation of X264

tried to install x264 and didnt change anything...

DId you guys get this to work?  If you look a couple lines up from this error, as I got the same thing, I also noticed a YASM error.  So Synaptic search for YASM and install.  Then rerun, and it works.

Hope that helps.  Converting vid now, just wish there was a way to do a complete dvd at one time, not each .vob file?

I haven't got one on the PSP yet, but assume that will work.

Also noticed to make sure to unmount the PSP before disconnect as that will cause errors.

:-D

---

### Post by mono-jo on 2009-04-09
help!!
 my psp does not want to connect
](*,) ](*,)

---

### Post by anjilslaire on 2009-04-09
Plug your PSP in via usb, and set it to USB mode. As mentioned, it should appear as a drive on your desktop, like any other storage device.

---

### Post by twooften on 2009-04-12
This is what I did... hope it helps someone...

****Download qpspmanager-2.0.2.tar.gz
****Extract Contents (one directory called qpspmanager-2.0.2
****Open terminal
****Navigate to extracted directory
****(I had to install some other stuff because I am running a fresh install)
sudo apt-get install libqt4-dev
////enter password
////bla bla bla
sudo apt-get install g++
////enter password
////bla bla bla
qmake qpspmanager.pro
make
////it has created a bin directory in the extracted directory.
////open, double click and enjoy...

---

