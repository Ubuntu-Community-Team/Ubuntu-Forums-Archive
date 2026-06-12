---
title: "Install Compiz Effects; Screensaver, Freewins, Atlantis2"
date: 2009-06-10
forum: Desktop Environments
---

### Post by xfearxnxloathing on 2009-06-10
********************[COLOR="Red"]**UPDATED**[/COLOR]***********************
all you need to do is check this link out
[http://forum.compiz.org/viewtopic.php?f=114&t=12012]("http://forum.compiz.org/viewtopic.php?f=114&t=12012")
        do not go below this line
**********************************************

[COLOR="Red"]This is once you've gotten compiz up, running and functional![/COLOR]  **UBUNTU** [COLOR="Red"]Jaunty Jackalope[/COLOR]

**Step 1**: Open Terminal and type: ```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev
```
(apparently you have to have dev stuff installed to use them..)

**Step 2**: Turn off Compiz! ((Compiz Switch) just for safety may work without doing so if you want to take a chance.)

**Step 3**: Create a folder to keep the plugin sources in: Open Terminal or type in same from above: ```
mkdir ~/compizplugins
``` then: ```
cd ~/compizplugins
```

**Step 4**: Download the plugin source code using git: Again with the terminal and type: ```
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/warlock/freewins
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
```

**Step 5**: Compile the individual plugins by switching to their directories and running make and make install: Terminal ```
cd ~/compizplugins/atlantis2
make
make install
cd ~/compizplugins/freewins
make
make install
cd ~/compizplugins/screensaver
make
make install
```

**Step 6**: Log out and back in to restart Compiz and your current session.  Next make your way to compiz-settings-manager and look under: Extras (screensaver), Effects (Cube Atlantis & Freely Transformable Windows (freewins)).

;)

---

### Post by xfearxnxloathing on 2009-06-10
some responses would be nice =P

work/doesn't work?!?!

---

### Post by overdrank on 2009-06-10
Moved to Desktop Environments

---

### Post by xfearxnxloathing on 2009-06-10
> **overdrank said:**
> Moved to Desktop Environments

sry  =]

---

### Post by sparazza on 2009-07-03
It works!\\:D/

For me the correct dependences are:
**compiz-fusion-bcop** instead of compiz-bcop and **git-core**

Sparazza

---

### Post by jbryant on 2009-09-27
Forgive a noob, but I'm getting an error when I try to make:
```
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by zcat on 2009-10-27
> **xfearxnxloathing said:**
> some responses would be nice =P

work/doesn't work?!?!

in the first apt-get install, compiz-bcop is now (jaunty) called compiz-fusion-bcop, and also might be an idea to put git-core in there as well so the next step works.

Also was the 'Auto Nice Daemon' package intended, or was that the word 'and' between the last two packages in the list? I've left it in because it does no harm..

As a single shell script (not tested yet but I hacked this up just now because I have several machines here and I'm lazy)

```

#!/bin/bash

sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev libglu1-mesa-dev and git-core
mkdir ~/compizplugins && cd ~/compizplugins

git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/warlock/freewins
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver

cd ~/compizplugins/atlantis2 && make && make install
cd ~/compizplugins/freewins && make && make install
cd ~/compizplugins/screensaver && make && make install


```

---

### Post by iPCGuy on 2009-11-19
how to turn off compiz?

---

### Post by xfearxnxloathing on 2010-01-08
> **iPCGuy said:**
> how to turn off compiz?

System>Administration>Synaptic Package Manager, type Compiz-Switch

---

### Post by jsearles on 2010-02-14
I did everything suggested above and this is the error:

Makefile:48: *** [ERROR] Compiz not installed.  Stop.

Can anyone help?

---

### Post by skod_alf on 2010-03-12
install the compiz-dev package. then it will work

---

### Post by aviramof on 2010-03-13
the first command should be fixed to:
```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev

```

---

### Post by xfearxnxloathing on 2010-06-02
> **aviramof said:**
> the first command should be fixed to:
```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev

```

thank you ;]

---

### Post by ethan1701 on 2010-07-17
> **jbryant said:**
> Forgive a noob, but I'm getting an error when I try to make:
```
make: *** No targets specified and no makefile found.  Stop.
```

I too am getting this error when trying to compile Freewins (Am not interested in and have not tried the others)
After fetching the files with git, the files I see in the freewins directory are:
AUTHORS
CMakeLists.txt
COPYING
freewins.xml.in
[COLOR="Blue"]src[/COLOR] (a directory)

there doesn't seem to be a make file. Is this presently missing from the repository?

-Ethan

---

### Post by nick_goodfate on 2010-07-26
> **ethan1701 said:**
> I too am getting this error when trying to compile Freewins (Am not interested in and have not tried the others)
After fetching the files with git, the files I see in the freewins directory are:
AUTHORS
CMakeLists.txt
COPYING
freewins.xml.in
[COLOR="Blue"]src[/COLOR] (a directory)

there doesn't seem to be a make file. Is this presently missing from the repository?

-Ethan

i m getting the same error :( pls some help...

---

### Post by realzippy on 2010-07-26
Cannot help you with that compiling problem....but
there is an easy way to install all compiz plugins (freewins included;
just tested,it works):

[http://forum.compiz.org/viewtopic.php?f=114&t=12012](http://forum.compiz.org/viewtopic.php?f=114&t=12012)

---

### Post by nick_goodfate on 2010-07-26
> **realzippy said:**
> Cannot help you with that compiling problem....but
there is an easy way to install all compiz plugins (freewins included;
just tested,it works):

[http://forum.compiz.org/viewtopic.php?f=114&t=12012](http://forum.compiz.org/viewtopic.php?f=114&t=12012)

:o thank you so much !!!

---

### Post by ericshaw.linux on 2010-08-25
when i run: git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
i get this output:

Initialized empty Git repository in /home/snake/compizplugins/atlantis2/.git/
fatal: The remote end hung up unexpectedly

please help i just want sum fishes in my cube..

---

### Post by xfearxnxloathing on 2010-08-31
> **realzippy said:**
> Cannot help you with that compiling problem....but
there is an easy way to install all compiz plugins (freewins included;
just tested,it works):

[http://forum.compiz.org/viewtopic.php?f=114&t=12012](http://forum.compiz.org/viewtopic.php?f=114&t=12012)

it's been a few years, this def needed updating, thank you! =]

---

### Post by Mi11z on 2010-09-25
Thanks i've bookmarked that link, really helpful and for futture reference ! :)

---

