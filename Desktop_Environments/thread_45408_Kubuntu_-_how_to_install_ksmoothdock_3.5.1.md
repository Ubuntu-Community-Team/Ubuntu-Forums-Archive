---
title: "Kubuntu - how to install ksmoothdock 3.5.1"
date: 2005-06-30
forum: Desktop Environments
---

### Post by oliwally on 2005-06-30
Ok, I know this is just playing around with eye-candy by those who have too much time or no social life, but hey - I'm on holidays !

How do I install ksmoothdock 3.5.1 in Kubuntu ? Is it even safe to do so, or will it seriously stuff up my Kubuntu installation ?

These here are the instructions from the KDE-look [ksmoothdock](http://kdelook.org/content/show.php?content=6585) website :

> NOTE***: In v3.5.1 the configuration will be saved in /.ksmoothdock/ksmoothdock-3.5.1.conf in your home directory.
The menu is in $HOME/.ksmoothdock/menu/

TO INSTALL: Unzip, cd to the directory ksmoothdock-3.5.1 then run:
./configure
make
su
make install

Then run:
ksmoothdock

(if when you run "ksmoothdock", nothing happens, then it is likely that your KDE dir is not standard. In this case, either:
- cd to the directory ksmoothdock-3.5.1/ksmoothdock, then run "./ksmoothdock", or
- Re-do the above sequence (./configure ...), but instead of "./configure", type:
./configure --prefix=/YOUR_KDE_DIR)

However, the standard installation method does not appear to work, and when doing the ./configure --prefix=/YOUR_KDE_DIR, I don't actually know where my KDE directory is. Doing a search brings up several files/folders on the system. I don't know which one to use.

So, does anyone know how to install it correctly? Please be detailed in your instructions. 

Thanks in advance

---

### Post by Xian on 2005-06-30
Have you tried using the [ksmoothdock_3.5.1_i386.deb](http://intranet.harlaut.net/debian/ksmoothdock/ksmoothdock_3.5.1_i386.deb) package?

---

### Post by ltmon on 2005-06-30
[QUOTE=oliwally]Ok, I know this is just playing around with eye-candy by those who have too much time or no social life, but hey - I'm on holidays !

How do I install ksmoothdock 3.5.1 in Kubuntu ? Is it even safe to do so, or will it seriously stuff up my Kubuntu installation ?

These here are the instructions from the KDE-look [ksmoothdock](http://kdelook.org/content/show.php?content=6585) website :



However, the standard installation method does not appear to work, and when doing the ./configure --prefix=/YOUR_KDE_DIR, I don't actually know where my KDE directory is. Doing a search brings up several files/folders on the system. I don't know which one to use.

So, does anyone know how to install it correctly? Please be detailed in your instructions. 

Thanks in advance[/QUOTE]

For Kubuntu you can just use --prefix=/usr to compile any kde program.  Also, instead of

> su
> make install

do this:

> sudo apt-get install checkinstall
> sudo checkinstall -D make install

and answer some questions (they're pretty easy).

This will actually create a .deb package of your own (wow wasn't that fun).  The advantage of that is that you can remove the package later with a lot more ease than if you simply installed it normally.

As mentioned, a premade deb is usually easier, but only if it's a Kubuntu package... most vanilla debian packages (like the one linked) won't work.

---

### Post by oliwally on 2005-06-30
> As mentioned, a premade deb is usually easier, but only if it's a Kubuntu package... most vanilla debian packages (like the one linked) won't work.

Yes, I'm a bit shy about using a non-ubuntu debian package.

> For Kubuntu you can just use --prefix=/usr to compile any kde program. Also, instead of

> su
> make install

do this:

> sudo apt-get install checkinstall
> sudo checkinstall -D make install

and answer some questions (they're pretty easy).

It didn't work. Installation failed.

Output of sudo ./configure --prefix=/usr
 was:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

Output of make was
```
make: *** No targets specified and no makefile found.  Stop.
```

Any ideas how to go about it from here or what the problem may be? Have I perhaps got the wrong files downloaded -for i686 rather than the 386 for my computer?

---

### Post by Feanor on 2005-06-30
You must have a C and C++ compiler installed on your system. Open synaptic (or kynaptic) and install gcc or gpp or g++ or all of these if you want.

---

### Post by oliwally on 2005-06-30
> You must have a C and C++ compiler installed on your system. Open synaptic (or kynaptic) and install gcc or gpp or g++ or all of these if you want.

There are so many different ones of those ! Which ones, specifically, do I install ?

I installed some of them and tried installing the ksmoothdock installation again, but no luck.

---

### Post by PhilippWollermann on 2005-06-30
Hi,

very easy. Just open a Konsole and do:

sudo apt-get install build-essential

This will get the basic developer tools installed. After that you probably need some KDE development libraries too...

sudo apt-get install libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev

I guess this should be sufficient. Please report back, if it works or not. :-)

Philipp

---

### Post by ltmon on 2005-06-30
[QUOTE=PhilippWollermann]Hi,

very easy. Just open a Konsole and do:

sudo apt-get install build-essential

This will get the basic developer tools installed. After that you probably need some KDE development libraries too...

sudo apt-get install libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev

I guess this should be sufficient. Please report back, if it works or not. :-)

Philipp[/QUOTE]

What he said.

---

### Post by oliwally on 2005-07-01
Cool - it worked. Thanks so much for your help. A buckedload of downloading and a screwed up Firefox installation later (easy to fix though)

**_Still have some problems though:_**

How do I make it so ksmoothdock starts up by itself, rather than me having to turn it on every session?

When adding shortcuts to the quick launch menu, I have not been able to add kfind from /usr/bin, although I have been able to add other shortcuts. Is there a limit to the number of shortcuts I can have (have seven, want to add more)?

Thanks again. Why don't they include the excellent info you've given me on the ksmoothdock info page - I bet lots of people would be asking the same question I did ! Or is it only reserved for experts like yourselves, while relative newbie knownixes like myself are left in the dark?

---

### Post by PhilippWollermann on 2005-07-01
Hi,

I'm glad that ksmoothdock works for you now. :-) I don't know why they do not publish an installation Howto, but maybe, it's because no-one asked them to do so. If I had an idea, where to put my "Mini-Howto", I would certainly do so.

There is a simple way to automatically start ksmoothdock - use the "Autostart" folder. Open a new Konqueror window and choose "Go" in the Menu, then click on "Autostart". Just drop a link to ksmoothdock there, and it should work.

I don't know why adding kfind to the quick launch menu didn't work. I'll install ksmoothdock myself and try it.

Philipp

---

### Post by oliwally on 2005-07-01
Wow that was easy indeed ! Thank you so much. I guess it's always easy when you know how.....

Just needed to mention  - this forum and it's contributers are fantastic ! I have received so much help already to my Kubuntu work. In fact, the whole Linux community as a whole seems to be really helpful. Well done everybody.

I'll keep watching this topic to see what happens to the additional items added to the start menu.

Thanks again ! Vielen Dank !

---

### Post by Plagued on 2005-07-03
Hello all,
  I am a total newb to (K)Ubuntu (and debian for that matter) and so far I am wholly impressed. I have been using Gentoo for the last several years and it is nice to setup a system without days of tweaking. Mostly everything is working swimmingly, but I would so like to have ksmoothdock.
  I have read through this form and when I do

```
./configure --prefix=/usr
``` 

I get an error at the end about not being able to find X includes. I have tried adding --with-includes=/usr/X11R6/include but no love.

I have been through the other steps in the forums (I already had the build utilities installed so that I could get my Cisco VPN client working), but always the same error. Any ideas?

---

### Post by Plagued on 2005-07-03
OK I got it ... somehow I overlooked the .deb that was mentioned early in this thread. That did the trick.

---

### Post by PhilippWollermann on 2005-07-04
If you'd like to compile it from source, you have to install the corresponding devel packages. If it doesn't find the X Includes, you have to see, which devel package may provide them.. my guess:

sudo apt-get install x-dev

Philipp

---

### Post by thagame on 2005-07-04
i dont know if it makes any difference but unless you unpack the file in a root environment you dont have to type sudo ./configure. just ./configure, make. then sudo make install.

---

### Post by PhilippWollermann on 2005-07-05
Hi thagame,

you're right - I didn't spot this one. sudo ./configure isn't necessary and may even cause permission problems. Either do it without sudo and only sudo when installing, or do it all as root (evil! ;)).

Philipp

---

### Post by oliwally on 2005-07-09
Well, the whole thing works very nicely for me now, except for not being able to add more items to start menu. It seems like there is a limit on how many items can be added. Does anyone have a solution?

Just on a user note - the smoothdock is very nice eye-candy, but I found it a bit slow to use. Access through the Kmenu is a lot faster. Still - I love the look of it.

---

### Post by trivialpackets on 2005-07-14
[QUOTE=oliwally]Well, the whole thing works very nicely for me now, except for not being able to add more items to start menu. It seems like there is a limit on how many items can be added. Does anyone have a solution?

Just on a user note - the smoothdock is very nice eye-candy, but I found it a bit slow to use. Access through the Kmenu is a lot faster. Still - I love the look of it.[/QUOTE]
 Screenshot?

---

### Post by Guillaumeb on 2006-09-03
Hello,

I am a REAL noob in Kubuntu. Actually I have installed KDE on Ubuntu. i'm vvery interested in installing ksmoothdock

Now I come from windows and im' not too familiar with prog installation.

in the Konsole I have done those steps mentionned above:
sudo apt-get install build-essential
and
sudo apt-get install libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev

I have the tar.gz file on my Hardrive. Now I have no idea what to do next.

Can someone guide me here? When trying to run the .deb file it says :
dependency not satisfiable: kdelibs4

I am really lost here how can I install this required dependency?

thank you so much

---

### Post by MontanaMax on 2006-12-26
I've been working on an install guide for the new version of KSmoothDock on Kubuntu - it's available at [https://help.ubuntu.com/community/Montanamax/KSmoothDock](https://help.ubuntu.com/community/Montanamax/KSmoothDock) and I believe your problem will be fixed in the first step:

```
sudo apt-get install kdebase-dev build-essential automake1.9
```

Please let me know if that doesn't work for you so we can figure it out and I can get the install guide updated.

Thanks,

- Jon

---

### Post by peacekpr on 2007-02-16
So I compiled KSmoothDock after resolving several dependencies with Qt and KDE.  It successfully compiled.  I ran 'ksmoothdock' for the first time with success and saw the configuration window.  I closed the configuration window to attempt to get the dock bar running.  Ksmoothdock immediately crashed and continues to crash with the following backtrace information:
```
Using host libthread_db library "/lib/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread 47611922057616 (LWP 19703)]
0x00002b4d83559c40 in nanosleep () from /lib/libc.so.6
#0  0x00002b4d83559c40 in nanosleep () from /lib/libc.so.6
#1  0x00002b4d83559a94 in sleep () from /lib/libc.so.6
#2  0x00002b4d805e6575 in KCrash::startDrKonqi () from /usr/lib/libkdecore.so.4
#3  0x00002b4d805fab07 in KCrash::defaultCrashHandler ()
   from /usr/lib/libkdecore.so.4
#4  0x00002b4d834f5510 in killpg () from /lib/libc.so.6
#5  0x0000000000000000 in ?? ()

```

I get lost when I see that.  It appears as though the problem is in libkdecore.so.4?  Anyone else seen this problem?  This is probably the problem that is mentioned when ksmoothdock is compiled using KDE libs 3.5.5.  Any suggestions?

---

### Post by iamhugeinjapan on 2007-02-16
From the[ Ksmoothdock page]("http://www.kde-look.org/content/show.php?content=6585"):

> 
It seems that KDE 3.5.5 breaks KSmoothDock, so if you really like KSmoothDock, do not upgrade to KDE 3.5.5


I'm not sure how it is affected by 3.5.6

---

