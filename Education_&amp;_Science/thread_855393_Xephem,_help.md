---
title: "Xephem, help?"
date: 2008-07-10
forum: Education &amp; Science
---

### Post by behindthestove on 2008-07-10
I downloaded XEphem into my home folder and I can't figure out how to get it to work. 

I'm not really the wisest in the way of computers, besides clicking. XEphem is the first open source program I have tried to download and I just switched to Ubuntu two days ago... I'm using 8.04...

I am sure there is something simple I am missing, help please?

---

### Post by ssam on 2008-07-10
for most software on ubuntu the repositories are the best place to get it.
[http://doc.ubuntu.com/ubuntu/switching/applications-installing.html](http://doc.ubuntu.com/ubuntu/switching/applications-installing.html)

xephem seems not to be in the repos because it is not free software (the GNU definition [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html) ). You are however allowed to download the source code, and build it for "personal use or for bona fide educational situations or research funded by public funds"

you could try these instructions
[http://jalvesaq.googlepages.com/xephem.html](http://jalvesaq.googlepages.com/xephem.html)
which should make and install a package for you. if it does not work please paste the error mesages into your reply, so we can figure out what went wrong.

---

### Post by g_rus on 2008-07-10
Today i follow this instructions [http://www.tc.umn.edu/~brams006/xephem_ubuntu.html](http://www.tc.umn.edu/~brams006/xephem_ubuntu.html)

But, in the part when say: "make MOTIF=/usr/lib/" better i do, te instruccionst on INSTALL file that say: "make MOTIF=../../libXm/linux86" for x86 system.

The steps are this (but of course read the link)
1.- check for this libraries on tour system: gcc lesstif2-dev ibc6-dev libxmu-dev make (Of course in Adept or Synaptic you can see)

2.- Doanload the Xepehm source from the site. Save in specific folder to use, for example, you can create a directory in your home called "Programs", and unzip here, you get a new directory called Xephem-3.7.3 (3.7.3 is the lastone version)

3.- Go to Xephem directory, the to "libz" directory, then, change te premission to write for the file called "Makefile" with this in a terminal: chmod +w Makefile

4.- Open in a editor (gedit, nano) the Makefile and be sure that at TOP of the file have this:
CC = gcc
CLDFLAGS = -g
CFLAGS = $(CLDFLAGS) -Wall -O2
LDFLAGS =

then some lines down, you can see this:
testzlib: testzlib.o libz.a
gcc $(LDFLAGS) -o testzlib testzlib.o libz.a

of course say "cc", change for "gcc", be sure that all is correctly, and save

5.- Change to directory.../xephem-3.7.3/GUI/xephem and then, type this instrucctions in terminal: make MOTIF=../../libXm/linux86
Will take 3 or 4 minutes, or less.

Then in that directory writte "./xephem" (without "", of course)and enjoy, of course you can put a entrance to xephem in your directory or a incon in your desktop. For some reason, to my, my icon on Menu, to run Xephem not have all libraries, but runing in terminal directo from the directory al work fine.
Good luck :D

---

### Post by kleeman on 2008-07-11
Here are some instructions that will produce a quality deb. To be prefeered imho

[http://jalvesaq.googlepages.com/xephem.html](http://jalvesaq.googlepages.com/xephem.html)

---

### Post by behindthestove on 2008-07-11
Thanks for your help! 

Most of those instructions were a little too advanced for my level of skill, but I showed them to my friend, and he got it done.

Xephem is working well.

---

### Post by Friqenstein on 2008-07-14
Hey all,

Long time linux user, first time Ubuntu poster.  :)

Ok, so after having already compiled and setup Xephem, this is what I'm getting:

I created a shortcut (menu item) so that I could launch it with all my other science applications form my menu. It launches the program just fine, however it's not complete.
What I mean by that is, when I try to set my location, the location table is completely empty. Or when I try to open the Data Table, it's blank as well. If I try to view any of the Data, or images (Sun, Moon, etc) it just crashes.
Now here is the weird part... if I open up my term and navigate to the xephem directory, go into the GUI/XEphem dir and run ./xephem the program runs and EVERYTHING works perfectly fine. All data, images, location tables, etc. All perfectly fine. how odd is that?

Any suggestions? I've tried recreating the link as a launchable from the desktop using the exact same path/command as I did in the terminal. NoGo. :confused:

Ideas?
Thanks.
L8rz

---

### Post by behindthestove on 2008-07-15
This is the script on my desktop that makes xephem work...

#!/bin/bash

( cd /home/greta/Desktop/xephem-3.7.3/GUI/xephem && /home/greta/Desktop/xephem-3.7.3/GUI/xephem/xephem )

---

### Post by Friqenstein on 2008-07-15
> **behindthestove said:**
> This is the script on my desktop that makes xephem work...

#!/bin/bash

( cd /home/greta/Desktop/xephem-3.7.3/GUI/xephem && /home/greta/Desktop/xephem-3.7.3/GUI/xephem/xephem )
Thanks for the reply.
I actually thought about trying that, but figured it would be the same result... I'll give it a shot and see.

Thanks.

---

### Post by Friqenstein on 2008-07-15
Ok. While trying to utilize that particular command line argument in the *Menu* shortcut, it kept telling me that **cd** isn't valid... strange I thought.

So instead this is what I did:
Used **vi** to make a small script with the following
```
cd /home-dir-to-xephem && ./xephem
```
then a **chmod +x** to make it executable.

So now in my *Menu*, I just have it call the script in my home directory and it all seems to work fine now.

---

### Post by ReFuSeD88 on 2008-07-16
great thread! thx

---

### Post by Oxnyx on 2008-10-05
All, 

I followed the instructions posted here:

[http://jalvesaq.googlepages.com/xephem.html](http://jalvesaq.googlepages.com/xephem.html)

All was going fine until I issued the following command:

dpkg-buildpackage -rfakeroot -uc -us

Everything appeared to be doing the right thing, untul I received this message:
~~~~~~~~~~~~~~~
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package xephem
dpkg-buildpackage: source version 3.7.2-1
dpkg-buildpackage: source changed by Jakson Alves de Aquino <jalvesaq@gmail.com>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: build-essential
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
~~~~~~~~~~~~~~~

I am not sure what is the best/most correct way to proceed. Should I back out (if so, how?)? Override? Any assistance will be most appreciated....

---

### Post by jalvesaq on 2008-10-08
I updated the building instructions. It should work again:
[http://jalvesaq.googlepages.com/xephem.html](http://jalvesaq.googlepages.com/xephem.html)

---

### Post by kharat on 2009-01-04
hi jalvesaq,

I am new to ubuntu and little old for debian, and planning to install xephem ([COLOR="Red"]thoroughly[/COLOR] used under suse 9.1).
I assume that all the commnand to be issued at prompt while an internet connection is on (wget htt... etc).
Presently using HH and edubuntu.
How can i be sure that the lib files are already available? I check /var/lib/../available, and couldnot find out lesstif2-dev libc6-dev libxmu-dev ect. Is it safe to assume that gcc and make must be installed?
I am highly interest in the package, and may not very [COLOR="Red"]prompt[/COLOR] in installing it, but will surely proceed.
vikas kharat.

---

### Post by jalvesaq on 2009-01-06
> **kharat said:**
> hi jalvesaq,
I assume that all the commnand to be issued at prompt while an internet connection is on (wget htt... etc).
Presently using HH and edubuntu.
How can i be sure that the lib files are already available? I check /var/lib/../available, and couldnot find out lesstif2-dev libc6-dev libxmu-dev ect. Is it safe to assume that gcc and make must be installed?
vikas kharat.

Hi,

Yes, most commands will work only if the computer is connected with the internet. The *-dev packages install header files (*.h) into /usr/include/. The headers are necessary to compile, but not to run the application. The command "apt-get install" retrieves the packages from the official repositories as well as all dependencies and installs them. Gcc and make are dependencies of build-essential. That's why it's not necessary to list them directly among the packages to be installed.

If you simply copy and paste each of the commands listed in the instructions, you should have xephem installed and accessible from the Ubuntu's Applications menu.  You can type in the terminal "man command" to know what they do. For example: "man dpkg-buildpackage".

---

### Post by rmls on 2009-01-25
Hi jalvesaq.

I followed your instructions and they worked a treat, 
thank you very much.

rmls

---

### Post by kharat on 2009-04-10
hi jalvesaq,

i copy pasted the commands at the prompt and everything went fine. I am now using xephemeris.
vikas

---

