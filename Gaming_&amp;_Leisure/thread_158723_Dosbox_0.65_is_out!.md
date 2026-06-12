---
title: "Dosbox 0.65 is out!"
date: 2006-04-11
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2006-04-11
For download: [http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download](http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download)

>     * 4/15/16/32bpp VESA mode support
    * Lot's of fixes for better vga compatibility
    * Improved CGA composite output
    * Added video capturing to avi
    * Improved screen updating for more speed
    * PCjr machine mode added
    * Speedup cpu cores and fix endian issues
    * FPU core speedup with assembly
    * Improved keyboard and bios handling
    * Lockfree mouse mode added again
    * Improved builtin dos with umbs and better fat support
    * Added VCPI emulation and fixed some issues with ems
    * Improved support for booter games
    * Modem and IPX support improved for multiplayer
    * Countless other bugfixes and features added


More goodies for us who loves old games :)

---

### Post by KingBahamut on 2006-04-11
Time to break out Kings Quest 1 and Thexder. 

=)

---

### Post by hizaguchi on 2006-04-12
I just compiled it this morning.  The video updates got Personal Designer running!  I can finally get rid of that Windows 98 machine at work!

---

### Post by Perfect Storm on 2006-04-12
Congratz!!!!
Diffently good news ^^

---

### Post by Olli on 2006-04-13
As I have some dear games plus my ten years old calendar on MSDOS, I have been using dosbox for years, both on different Win and Linux platforms, the last but one version being 0.63.

I grasped the new version as soon as its publishing was announced, downloaded the source, compiled it to a .deb file. and installed it. Thereafter every time I upgrade my Ubuntu (5.10) I get an error message telling me that libaa1-dev -- that had to be installed as libsdl1.2-dev was dependent on it -- is not configured. I uninstalled dosbox-0.65, and tred to reinstall dosbox-0.63. However. the error message persists:

 Esiräätälöidään paketteja...
Selecting previously deselected package dosbox.
(Reading database ... 78821 files and directories currently installed.)
Unpacking dosbox (from .../dosbox_0.63-2_i386.deb) ...
Setting up libaa1-dev (1.4p5-28ubuntu3) ...
install-info: Tiedostoa tai hakemistoa ei ole for Libraries
dpkg: error processing libaa1-dev (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dosbox (0.63-2) ...

Errors were encountered while processing:
 libaa1-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Telling (in Finnish) that the file or dirctory libaa1-dev is not available for Libraries.

Code:
dpkg -l > /home/olli/Downloads/asennetut && less asennetut 

gives
ri  libaa1-dev                                 1.4p5-28ubuntu3     ascii art library, development kit

(I tried to reinstall libaa1-dev, but apparently without success)

Anyone knows and knows to explain, what this means and how to get it corrected?

---

### Post by Perfect Storm on 2006-04-14
Have you tried making a new compile from the souce after you upgrade? When you said upgrade do you mean distro upgrade from Hoary to breezy or breezy to dapper?
Try first with flushing the apt-get cache:
```
sudo apt-get clean
```
and try again.

But as I recall it I had problems with the same file in Breezy.

---

### Post by Olli on 2006-04-14
[QUOTE=Artificial Intelligence]Have you tried making a new compile from the souce after you upgrade? When you said upgrade do you mean distro upgrade from Hoary to breezy or breezy to dapper?
Try first with flushing the apt-get cache:
```
sudo apt-get clean
```
and try again.

But as I recall it I had problems with the same file in Breezy.[/QUOTE]

With upgrade I mean 

apt-get update && apt-get dist-upgrade

I'll check what cleaning the cache will do, thanks for suggestion!

---

### Post by Mathias-K on 2006-04-15
I didn't even know that Dosbox was available in Ubuntu. Thanks for the heads up  :)

I got no clue of compiling, so i'll try 0.63-2 out today.

---

### Post by Perfect Storm on 2006-04-15
Uninstall the previous dosbox first.
Save the dosbox source to your desktop. [http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download](http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download)

```
sudo apt-get install build-essential libsdl1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev
cd Desktop
tar zxvf dosbox-0.65.tar.gz
cd dosbox-0.65
./configure
make
sudo make install

```

---

### Post by Mathias-K on 2006-04-15
[QUOTE=Artificial Intelligence]Uninstall the previous dosbox first.
Save the dosbox source to your desktop. [http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download](http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download)

```
sudo apt-get install build-essential libsdl1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev
cd Desktop
tar zxvf dosbox-0.65.tar.gz
cd dosbox-0.65
./configure
make
sudo make install

```[/QUOTE]

Whew.. Compiling sure isn't for new users.. :)

I uninstalled the dosbox package, downloaded the tarball and pasted your commands all at one time into Konsole, which gave me this:

```
sdl-net1.2-dev libsdl-sound1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
mathias@MathiasKubuntu:~$ cd Desktop
mathias@MathiasKubuntu:~/Desktop$ tar zxvf dosbox-0.65.tar.gz
dosbox-0.65/
dosbox-0.65/README
dosbox-0.65/acinclude.m4
dosbox-0.65/configure.in
dosbox-0.65/aclocal.m4
dosbox-0.65/Makefile.am
(....) a lot of such lines.. :)
mathias@MathiasKubuntu:~/Desktop$ cd dosbox-0.65
mathias@MathiasKubuntu:~/Desktop/dosbox-0.65$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
mathias@MathiasKubuntu:~/Desktop/dosbox-0.65$ make
make: *** No targets specified and no makefile found.  Stop.
```

I have absolutely no clue as to what's going on here. Can you see what i'm doing wrong?

Why don't they just make an executable file that is cross-distro, perhaps just requiring a 2.6-based kernel or something. Sounds much easier to me :)

---

### Post by Perfect Storm on 2006-04-15
> The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed

As you see the problem lies here
Try with refreshing your sourcelist
```
sudo apt-get update
```

Also it seems it havn't installed build-essential. Try again.

By the way how does your sourcelist looks like?
```
 sudo gedit /etc/apt/sources.list
```

---

### Post by Mathias-K on 2006-04-15
[QUOTE=Artificial Intelligence]As you see the problem lies here
Try with refreshing your sourcelist
```
sudo apt-get update
```

Also it seems it havn't installed build-essential. Try again.

By the way how does your sourcelist looks like?
```
 sudo gedit /etc/apt/sources.list
```[/QUOTE]

Hmm... it stil doesn't really work. A quick kdesu kata /etc/apt/sources.list gave me this:

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

## created by arniesourcewrite
```

---

### Post by Perfect Storm on 2006-04-15
Back it up:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_Backup
sudo gedit /etc/apt/sources.list
```

and put this in instead:
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# Bleeding edge wine packages (sources)
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

# OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free


save it and exit.

then
```
sudo apt-get update
```

---

### Post by Mathias-K on 2006-04-17
Nice work. I'll have a look at it when i'm done making my homework :)

---

### Post by Stinger on 2006-04-18
[QUOTE=Artificial Intelligence]Uninstall the previous dosbox first.
Save the dosbox source to your desktop. [http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download](http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download)

```
sudo apt-get install build-essential libsdl1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev
cd Desktop
tar zxvf dosbox-0.65.tar.gz
cd dosbox-0.65
./configure
make
sudo make install

```[/QUOTE]

Thanks for the nice instructions , just what I needed to install the latest version of dosbox.
The Speed is a lot better with the new version , I can play Hexen without stuttering sound now.
As you can see , I use [Dosboxgui]("http://www.waszumclique.de/dosboxgui/") , makes life a whole lot easier when you have a danish keyboard like mine.](*,) 
Thanks again. 
:mrgreen:

---

### Post by DoktorSeven on 2006-04-18
Thanks for the DosboxGui link.  Very nice.

Dosbox isn't hard to configure but when I'm lazy this is simpler :)

---

### Post by engineering.concepts on 2006-05-03
Thanks for the step by step instructions and link to dosboxGUI - very nice programs.
Here is a cool link to tons of DOS games. Some free some demo

[http://www.dosgamesonline.com/index/list/all/all](http://www.dosgamesonline.com/index/list/all/all)

Use the link on the left hand side to narrow down the search. (action, adventure, etc.)

I have tried only a few dos games from this site, but everything works prefectly!!!:D

---

### Post by DarkMageZ on 2006-05-13
i've made a package for ubuntu dapper (might work in breezy as well) for DosBox 0.65, just not sure where to host it. could host it on my work's server, but that could cost me my job, so for the moment, if u want the package, message me on freenode.

if someone is willing to host the package message me on freenode as well :)

---

### Post by Perfect Storm on 2006-05-14
You can send it to me. I'll see if I can find a place to host it.

---

### Post by siriusnova on 2006-06-06
can anyone please host the Dosbox 0.65 deb file? 

id like to use it instead of compiling from source :)

---

### Post by DarkMageZ on 2006-06-07
i emailed the package to artifical intelligence awhile back, not sure what happened, maybe filtered as spam. i still have the package available for x32, just message me on freenode. or leave a message here if u know where i could host it (under 500KB, including my gpg signature)

---

### Post by Mathias-K on 2006-06-07
I just compiled Dosbox 0.65 using Artificial Intelligence's method..

My console was attacked by an avalanche of wierd geekspeek :mrgreen:  But it works now, so thanks a lot :)

As i have no real clue to neither packaging nor compiling, I'd like to ask if it would be difficult to just include a .Deb file on the Dosbox website or make a repository?

---

### Post by warjowuch on 2006-06-13
yeah, i'm looking for a package as well. Does AI's method make a deb?
HopefullyI can play gta1 again with my friends :-) 0.63 does not have network-support...

---

### Post by siriusnova on 2006-06-13
is a deb available? i would like to download it if it is, i will host the deb too on my server for anyone that wants it.

---

### Post by jonboy99 on 2006-06-13
[QUOTE=siriusnova]is a deb available? i would like to download it if it is, i will host the deb too on my server for anyone that wants it.[/QUOTE]

Hmm, try this.  First time I have made a deb package from source though so not sure if it's worked.

[dosbox package]("www.jonbrookes.dsl.pipex.com/dosbox-0.65_0.65-1_i386.deb")

---

### Post by warjowuch on 2006-06-14
Any positive experiences with your package?
THanks for trying/doing BTW!

---

### Post by leech on 2006-06-14
What's really interesting is outside of here, the only debian package I could find was actually for the freebsd kernel distro of Debian.

[http://io.debian.net/~tar/debian/dosbox/](http://io.debian.net/~tar/debian/dosbox/)

Though theoretically one should be able to take the files here and create a Linux i386 version.  Though it does sound kind of fun to play around with FreeBSD + Debian, along with maybe OpenSolaris + Debian.  Though I don't think either has quite as much hard ware support, but of course I could be wrong.

Leech

---

### Post by jonboy99 on 2006-06-14
Has anyone tried the package I compiled and linked to?

---

### Post by warjowuch on 2006-06-15
Did you? :-)if it works flawless, I am the next, but maybe I will just do it, the risk can't be that big if it is broken somehow

---

### Post by FredB on 2006-06-15
[QUOTE=Artificial Intelligence]For download: [http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download](http://prdownloads.sourceforge.net/dosbox/dosbox-0.65.tar.gz?download)



More goodies for us who loves old games :)[/QUOTE]

yes ! I will play again to these good old genuine Doom / Doom 2 versions ;)

---

### Post by Perfect Storm on 2006-06-15
For those who are interested in a howto of dosbox with dosbox-gui I wrote one at Ubuntu Gamers Arena: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=23&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=23&Itemid=63)

---

### Post by Perkins on 2006-09-29
Read carefully and it's fairly obvious.  ;) 

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH

You should be able to get one of those from the repository with minimal fuss.  Then try it again and look for more lines complaining about not having something it needs.  Eventually you'll have it all and it should work.

Have fun.

---

### Post by valnar on 2006-11-11
Sorry - n00b here.  Would anyone be willing to make a .deb of one of the later CVS builds of DOSBox?

Here are some that I like on Windows.  It would be nice to get it on Linux too.
[http://vogons.zetafleet.com/viewtopic.php?t=9306](http://vogons.zetafleet.com/viewtopic.php?t=9306)

Robert

---

### Post by edemark on 2006-11-12
In my point of view the easiest was to start using dosbox 0.65 is downloading  the DosBox Game Launcher that has the cvs version built in so you really just click a bit and go. Seting up games is just easy and straightforward. So if you have just some old dos game that you want to play or you are up to download some to try out than do that so with GBGL.
here is the link to follow

[http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/)

good playing

pd dbgl uses java so you have to have working java to be able to use it

---

### Post by Perfect Storm on 2006-11-12
Is it better than dosbox gui?

---

### Post by edemark on 2006-11-13
the truth is that i have not tried dosbox gui. I could say that dbgl is that good that i have never wanted to try anything else but i guess that i did not try dosbox gui as i was lazy. Though anything i have tried to install (but Red Alert 1) worked flawlessly. Other than that i must mention that setting up the games is transparent and straightforward so in one word easy. 
One thing i have not tried in dbgl is installing games (sadly i have lost my imperium galactica cds :-( and this days mainly using cd-rip versions downloaded from the net, but i will try to look for some dos cd to try installing.

---

### Post by Stinger on 2006-12-10
> **Artificial Intelligence said:**
> Is it better than dosbox gui?

It has a lot more options and includes dosbox cvs so you don't need the dosbox package :-D 
[dosboxgui]("http://www.waszumclique.de/dosboxgui/") is good but [DosBox Game Launcher]("http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/") is better in my opinion.

---

### Post by Larsen on 2007-01-19
Dosbox 0.65 just showed up in my updates manager.

Wow, Speed increase and then some.
Big hug to the maintainers.

Larsen

---

### Post by jonboy99 on 2007-01-20
Thanks for the heads up!  I'd not been able to compile it on my core duo for some reason, and microprose formula 1 grand prix was way too slow with tarmac textures on  :biggrin:

---

### Post by valnar on 2007-01-20
Even DosBox 0.65 is old.  I would update it further with one of the various after release builds.  A lot has been done since then.

Robert

---

### Post by Number6 on 2007-01-23
Yea I recently got the update as well but I get problems with sound when i try to run it:

scotty@Logopolis:~$ dosbox
CONFIG:Loading settings from config file dosbox.conf
ALSA lib seq_hw.c:456: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none

Man I hate it when that happens! I assume something else has control and I need to tell dosbox to use it or something?

---

### Post by Perfect Storm on 2007-03-02
> **valnar said:**
> Even DosBox 0.65 is old.  I would update it further with one of the various after release builds.  A lot has been done since then.

Robert

Aye, I just grabbed 0.70 through CVS and testing it.

---

### Post by yabbadabbadont on 2007-03-03
> **Artificial Intelligence said:**
> Aye, I just grabbed 0.70 through CVS and testing it.

Is there any reason why you grabbed it from CVS as apposed to just downloading the 0.70 release tar.gz file?  (or was it released after you pulled it out of CVS?)

---

### Post by Perfect Storm on 2007-03-03
It was before you could get it in tarball.

---

### Post by yabbadabbadont on 2007-03-03
After I posted that, I realized how long ago your previous post was...  :oops:

Perhaps you can help with a different issue.  Do you have a current link for dosboxgui?  The ones in this thread are broken.  (or do you use a different frontend these days?)

Edit: By the way, the link in your signature to "Ubuntu Gamers Arena" points to a server that appears to have been hacked...  :?
Edit2: The link to the Dosbox with Dosboxgui howto also appears to have been hacked.:mad:

---

### Post by Perfect Storm on 2007-03-03
We are under heavy bombardement by hackers at the moment, so I can't say when we'll be up and running again or if all the game howto's I wrote can be safe.

---

