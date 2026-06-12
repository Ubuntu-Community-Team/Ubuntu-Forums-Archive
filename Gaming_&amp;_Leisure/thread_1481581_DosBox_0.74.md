---
title: "DosBox 0.74"
date: 2010-05-12
forum: Gaming &amp; Leisure
---

### Post by kinkinkijkin on 2010-05-12
I downloaded it, I extracted it, but I can't use or install it. Help?(I use Ubuntu 10.04)

---

### Post by kinkinkijkin on 2010-05-12
Really, please help me. Just tell me how to run DosBox after extracting the tar.gz file so that I may emulate like crazy and use the boot feature to boot windows from here in Ubuntu, or rise larger than windows and run Minix.

---

### Post by achase79 on 2010-05-12
just install it from the repositories using synaptic package manager

---

### Post by ELD on 2010-05-12
> **achase79 said:**
> just install it from the repositories using synaptic package manager

+ This.

Also for your posts try actually telling us what happens. What have you tried, did you try it in a terminal window (if you don't know how to do that...google it).

It pains me every time i see a "omg help me x doesn't work" type of post where no information is given.

DosBox is available in Software Centre as well.

---

### Post by achase79 on 2010-05-12
I believe kinkinkijkin downloaded the source and would have to compile and install from it to use that download.  And from another post, didn't know about synaptic package manager.

---

### Post by djhk on 2010-06-03
DosBox 0.74 is currently not available via the channel.
Only 0.73 is available.

---

### Post by rCXer on 2010-06-03
Try this...
```

sudo apt-get install build-essential autoconf automake
sudo apt-get build-dep dosbox
wget "http://downloads.sourceforge.net/project/dosbox/dosbox/0.74/dosbox-0.74.tar.gz"
tar -xvf dosbox-0.74.tar.gz
cd dosbox-0.74
./autogen.sh
./configure
make
sudo make install

```

---

### Post by CharmyBee on 2010-06-04
> **rCXer said:**
> Try this...
```

tar -xvf dosbox-0.74.tar.gz
cd dosbox-0.7**3**

```

Oops?

---

### Post by rCXer on 2010-06-04
Fixed it.  Thanks

---

### Post by sunshinecorp on 2010-07-11
The code worked beautifully and DOSBox 0.74 has been flawlessly installed on my system (Lucid). A theoretical question: how can I remove it, since the package doesn't appear on the software center or on synaptics? Thanks.

---

### Post by kroq-gar78 on 2010-07-25
> **rCXer said:**
> Try this...
```

sudo apt-get install build-essential autoconf automake
sudo apt-get build-dep dosbox
wget "http://downloads.sourceforge.net/project/dosbox/dosbox/0.74/dosbox-0.74.tar.gz"
tar -xvf dosbox-0.74.tar.gz
cd dosbox-0.74
./autogen.sh
./configure
make
sudo make install

```

when i do ```
./configure
``` it says:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
**checking whether the C compiler works... no**
configure: error: in `/media/TOSHIBAEXT/downloads/linux/dosbox-0.74':
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

my gedit cannot open 'config.log'. it says something similar to 'cannot detect character encoding'

any help would be appreciated.

sincerely,
kroq-gar78 (ubuntu 10.04 lucid lynx)

---

### Post by ucal on 2010-07-25
> **sunshinecorp said:**
> The code worked beautifully and DOSBox 0.74 has been flawlessly installed on my system (Lucid). A theoretical question: how can I remove it, since the package doesn't appear on the software center or on synaptics? Thanks.

```
cd dosbox-0.74
sudo make uninstall
```

I think.

---

### Post by kroq-gar78 on 2010-07-26
i really want to use 0.74 instead of my .73 without using wine

---

### Post by Perfect Storm on 2010-07-26
You can just use Dosbox Game Launcher it comes with 0.74: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
It makes it very easy to play dos game and you can set up different settings etc. for each games.

---

### Post by kroq-gar78 on 2010-07-26
thanks for the info. I'll try to set up a few games now :D

UPDATE: whenever i try to create a new profile, it says it can't find the dosbox .74 conf file. should i keep going and forget it?

---

### Post by Perfect Storm on 2010-07-26
First make sure that sun java is installed.

Then;

**64-bit**
```
mkdir -p ~/.dosbox/Launcher
cd ~/Desktop
wget http://members.quicknet.nl/blankendaalr/dbgl/download/dbgl069_64bit.tar.gz
tar zxfv dbgl069_64bit.tar.gz -C ~/.dosbox/Launcher
```


**32-bit**
```
mkdir -p ~/.dosbox/Launcher
cd ~/Desktop
wget http://members.quicknet.nl/blankendaalr/dbgl/download/dbgl069.tar.gz
tar zxfv dbgl069.tar.gz -C ~/.dosbox/Launcher
```


Now make a launcher for it;
```
alacarte
```

**Name:** Dosbox Game Launcher
**Command:** sh -c "cd ~/.dosbox/Launcher && ./dbgl" 

**Comment:**Dosbox with Game Launcher. An application to run dos programs and games.

---

### Post by kroq-gar78 on 2010-08-03
thanks for the launcher info. dosbox is awesome!

---

### Post by Junkieman on 2010-08-03
> **kroq-gar78 said:**
> when i do ```
./configure
``` it says:

```
**checking whether the C compiler works... no**
configure: error: in `[COLOR="Red"]**/media/TOSHIBAEXT/downloads/linux/dosbox-0.74**[/COLOR]':
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

Could it be that you're compiling on an external drive that has the NOEXEC flag set? I'm just guessing here, I have no experience compiling on an external drive and could be wrong. I usually put the source in /usr/src, or in ~/src and compile from there.

> **kroq-gar78 said:**
> my gedit cannot open 'config.log'. it says something similar to 'cannot detect character encoding'
config.log probably contains non-alphanumeric characters, you can try view it with ```
cat config.log | more
```

---

### Post by kroq-gar78 on 2010-08-03
ah thanks AI for dbgl and junkieman for telling me to NOT compile on an external drive.

also, how do I move the compiled dbox074 program from directory to directory? also, how do i remove that stuff i got when i did```
sudo apt-get build-dep dosbox
```
I'm running a little low on space so I would like to remove it.

thanks for all the help!

---

