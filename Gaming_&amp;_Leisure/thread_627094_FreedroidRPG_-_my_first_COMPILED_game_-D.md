---
title: "FreedroidRPG - my first COMPILED game :-D"
date: 2007-11-29
forum: Gaming &amp; Leisure
---

### Post by perixx on 2007-11-29
Jahoouuuuu !!!!!

I finally did it!! Compiled my first program -- freedroidRPG \\:D/

I must say, it was much less refusing to a compilation than other (much smaller) programs I tried... though it was SOME effort (for a newbie like me)!


Now that I've made a .deb package out of it  - can I share this with others, or is it specifically designed for my hardware (AMD 64 x2 / ATI x1950gt / ASUS A8R-MVP) and OS, Xubuntu 7.04?

=]]]

perixx

---

### Post by MickLionheart on 2007-11-29
It *might* be optimized for your system, but it should run on other x86 processors just fine

---

### Post by wishyjr on 2007-11-30
so.. er... like, y'know... wanna tell us about this program/game of yours? Do you want anyone to try it out? Gotta a link there champ? It has the word 'droid' in it so im interested :)

---

### Post by perixx on 2007-12-01
So, is there a way to add a .deb package to the official game repositories? Would they confirm to this? Whom would I have to contact for that?


FREEDROID comes in 2 flavours, wishyjr!

While 'Freedroid' is a really good and original-looking remake of the famous 'Paradroid' game on the C64,
'**[COLOR="Blue"]FreedroidRPG[/COLOR]**' is sort of an isometric RPG (cool graphics & atmosphere!) with Tux as a protagonist. 

**The story in short:**
> After 3 decades, MS finally has succeded and taken over the open-source licence, thus fully controlling the software production on the whole planet - installing their OS to robots all over the world! Shortly after that, a bloody revolution of the bots nearly wipes humankind from earth's face... 
one but last hope - to wake Tux from his decade-long lasting cryo-stasis...

[http://freedroid.sourceforge.net]("http://freedroid.sourceforge.net")

I've been doing some level-design for the game myself so far - contributors for level-design, sounds/graphics and coding are welcome to join in!  ;)


perixx

---

### Post by Vadi on 2007-12-01
You make a bug report in ubuntu, and tag it with "[needs-packaging]" - search for similar reports first so you get an idea of what to write in it.

---

### Post by Nevon on 2007-12-01
So how about sharing that nice .deb-package? I tried to compile freedroidrpg before, but it didn't work.

---

### Post by perixx on 2007-12-01
Hello again!

I'd really like to share my .deb package, but I can't upload it as attachment, maybe it's too large (96MB)... I have no idea, where else to put it!


Here are some Debian packages availible, though I'm not sure if they'll work - at least you'll gonna need a lot of the additional dependent packages listet there, the .deb is much too small!
[http://packages.debian.org/unstable/games/freedroidrpg]("http://packages.debian.org/unstable/games/freedroidrpg")

For future compilations of the latest FreedroidRPG source and other games, see the great site of Artificial Intelligence:
[http://gaming.gwos.org/doku.php/guides:freedroidrpg]("http://gaming.gwos.org/doku.php/guides:freedroidrpg")


The packages I installed during the compilation (as far as I can remember):

```
buid-essential
dctrl-tools (2.9.3build1)
debhelper (5.0.42ubuntu1)
dh-buildinfo (0.9)
dpkg-dev (1.13.24ubuntu6)
exim4 (4.63-11build1)
exim4-base (4.63-11build1)
exim4-config (4.63-11build1)
exim4-daemon-light (4.63-11build1)
g++ (4:4.1.2-1ubuntu1)
g++-4.1 (4.1.2-0ubuntu4)
gettext (0.16.1-1ubuntu2)
grep-dctrl (2.9.3build1)
html2text (1.3.2a-3)
intltool-debian (0.35.0+20060710.1)
libc6-dev (2.5-0ubuntu14)
libstdc++6-4.1-dev (4.1.2-0ubuntu4)
linux-libc-dev (2.6.20-16.32)
po-debconf (1.0.8)
sbuild (0.52)
cpp-3.4 (3.4.6-5ubuntu1)
g++-3.4 (3.4.6-5ubuntu1)
g77 (4:3.4.6-20ubuntu1)
g77-3.4 (3.4.6-5ubuntu1)
gcc-3.4 (3.4.6-5ubuntu1)
gcc-3.4-base (3.4.6-5ubuntu1)
gcc-4.1-locales (4.1.2-0ubuntu4)
gcc-4.1-source (4.1.2-0ubuntu4)
libg2c0 (1:3.4.6-5ubuntu1)
libg2c0-dev (1:3.4.6-5ubuntu1)
libstdc++6-dev (3.4.6-5ubuntu1)
libglib1.2 (1.2.10-17build1)
libglib1.2-dev (1.2.10-17build1)
libgtk1.2 (1.2.10-18)
libgtk1.2-common (1.2.10-18)
libgtk1.2-dev (1.2.10-18)
libatk1.0-dev (1.18.0-0ubuntu1)
libgtk2.0-dev (2.10.11-0ubuntu3)
libxcursor-dev (1:1.1.8-1)
libxext-dev (2:1.0.3-1build1)
libxfixes-dev (1:4.0.3-1)
libxi-dev (2:1.1.0-1build1)
libxinerama-dev (2:1.0.1-4build1)
libxrandr-dev (2:1.2.0-3ubuntu1)
x11proto-fixes-dev (1:4.0-0.1ubuntu2)
x11proto-randr-dev (1.2.1-1)
x11proto-xext-dev (7.0.2-5ubuntu1)
x11proto-xinerama-dev (1.1.2-4ubuntu1)
libcairo2-dev (1.4.2-0ubuntu1)
libexpat1-dev (1.95.8-3.4build1)
libflac-dev (1.1.2-5ubuntu2.1)
libfontconfig1-dev (2.4.2-1ubuntu1)
libfreetype6-dev (2.2.1-5ubuntu1.1)
libgl1-mesa-dev (6.5.2-3ubuntu8)
libglib2.0-dev (2.12.11-0ubuntu1)
libglu1-mesa-dev (6.5.2-3ubuntu8)
libglu1-xorg-dev (1:7.2-0ubuntu11)
libice-dev (2:1.0.3-1build1)
libjpeg62-dev (6b-13)
libmikmod2 (3.1.11-a-6ubuntu3)
libmikmod2-dev (3.1.11-a-6ubuntu3)
libogg-dev (1.1.3-2ubuntu2)
libpango1.0-dev (1.16.2-0ubuntu1)
libparagui1.0c2a (1.0.4-12)
libphysfs-1.0-0 (1.0.0-5)
libpng12-dev (1.2.15~beta5-1ubuntu1.1)
libsage-dev (0.1.2-1ubuntu1)
libsage0 (0.1.2-1ubuntu1)
libsdl-console (1.3-4)
libsdl-console-dev (1.3-4)
libsdl-gfx1.2-4 (2.0.13-3)
libsdl-gfx1.2-dev (2.0.13-3)
libsdl-image1.2 (1.2.5-2)
libsdl-image1.2-dev (1.2.5-2)
libsdl-mixer1.2 (1.2.6-1.1build1)
libsdl-mixer1.2-dev (1.2.6-1.1build1)
libsdl-net1.2 (1.2.5-7)
libsdl-net1.2-dev (1.2.5-7)
libsdl-pango-dev (0.1.2-1)
libsdl-pango1 (0.1.2-1)
libsdl-sge (030809dfsg-1ubuntu1)
libsdl-sge-dev (030809dfsg-1ubuntu1)
libsdl-sound1.2 (1.0.1-12build1)
libsdl-sound1.2-dev (1.0.1-12build1)
libsdl-stretch-0-2 (0.2.3-7)
libsdl-stretch-dev (0.2.3-7)
libsdl-ttf2.0-0 (2.0.8-3build1)
libsdl-ttf2.0-dev (2.0.8-3build1)
libsdl1.2-dev (1.2.11-7ubuntu1)
libsm-dev (2:1.0.2-1build1)
libsmpeg-dev (0.4.5+cvs20030824-1.9build1)
libsmpeg0 (0.4.5+cvs20030824-1.9build1)
libspeex-dev (1.1.12-3)
libtiff4-dev (3.8.2-6)
libtiffxx0c2 (3.8.2-6)
libvorbis-dev (1.1.2.dfsg-1.2ubuntu2)
libvorbisenc2 (1.1.2.dfsg-1.2ubuntu2)
libx11-dev (2:1.1.1-1ubuntu3)
libxau-dev (1:1.0.3-1)
libxdmcp-dev (1:1.0.2-1)
libxft-dev (2.1.12-1)
libxrender-dev (1:0.9.1-3)
mesa-common-dev (6.5.2-3ubuntu8)
pkg-config (0.21-1build1)
x11proto-core-dev (7.0.10-1)
x11proto-input-dev (1.4.1-1)
x11proto-kb-dev (1.0.3-2ubuntu1)
x11proto-render-dev (2:0.9.2-4ubuntu1)
xtrans-dev (1.0.3-1)
zlib1g-dev (1:1.2.3-13ubuntu4)
```

As for I'm not sure, which of these actually were necessary and I had to use the 'shotgun' method due to lack of knowledge, I'm perfectly sure there's a lot to be stripped... Maybe I'm gonna uninstall all of these packages again and try once more with the info on the Debian-site. After placing the unpacked files into a directory, I opened a terminal there. While trying to start ./configure over and over again, I managed to get further each time and installed the assumed missing dev-packages (and some more) via Synaptic, according to the error-output (was not easy to guess sometimes) |-}. 

Since I wanted to make a .deb package for later uninstallation, I decided to do a 'sudo checkinstall' instead of 'make install' - this led to further problems in the first place, so some of the packages here are to be addressed to checkinstall. After giving a description to the package at the first run, installation didn't finish and nothing was installed - so I had to investigate furtherly.

```
Surely needed are: 
- build-essential
- the compilers gcc, g++,... (maybe not g77 or all versions)
- libsdl1.2-dev (1.2.11-7ubuntu1)
- libgtk1.2 (1.2.10-18)
- libgtk1.2-common (1.2.10-18)
- libgtk1.2-dev (1.2.10-18)

Likely needed:
libg2c0 (1:3.4.6-5ubuntu1)
libg2c0-dev (1:3.4.6-5ubuntu1)
libstdc++6-dev (3.4.6-5ubuntu1)
libglib1.2 (1.2.10-17build1)
libglib1.2-dev (1.2.10-17build1)
libgtk2.0-dev (2.10.11-0ubuntu3)
debhelper (5.0.42ubuntu1)
dh-buildinfo (0.9)
gettext (0.16.1-1ubuntu2)
libc6-dev (2.5-0ubuntu14)
libstdc++6-4.1-dev (4.1.2-0ubuntu4)
linux-libc-dev (2.6.20-16.32)
sbuild (0.52)
```

Sorry if I write some crap here, folks, but I simply don't know better - t'was my first compilation and I had to guess a lot of things! Maybe you would do with only 1/4 of all that stuff and mainly with only the -dev packages - you got to try for yourself! :]


perixx

---

### Post by dfreer on 2007-12-02
You should be able to run the ldd command on the game binary, to see which shared libraries it is using:

```
ldd ./freedroidrpg
```

EDIT: I'm a bit confused. Did you code this program yourself, or are you just compiling it?

---

### Post by Beren Camlost on 2007-12-02
> **dfreer said:**
> EDIT: I'm a bit confused. Did you code this program yourself, or are you just compiling it?

He is just compiling it. And he is proub of it ;) I was too the first time I managed to compile a program. I like this tread and his input here, and also his efforts of making a .deb of it. I have a lot to learn in that department :)

---

### Post by Nevon on 2007-12-02
Heh, I managed to compile it too! I feel like a h4xx0r :P
Actually, I followed this guide [http://gaming.gwos.org/doku.php/guides:freedroidrpg](http://gaming.gwos.org/doku.php/guides:freedroidrpg)
It worked perfectly!

---

### Post by dfreer on 2007-12-02
> **Beren Camlost said:**
> He is just compiling it. And he is proub of it ;) I was too the first time I managed to compile a program. I like this tread and his input here, and also his efforts of making a .deb of it. I have a lot to learn in that department :)

See, now I thought it was the OP's first *program*, and then I go to look at the screenshots... :shock: Definitely not the "Hello, world" I remember!

Nice job on compiling and making your first .deb!

---

### Post by perixx on 2007-12-02
```
ldd ./freedroidRPG
```

MANY THANKS, dfreer!!
This command is really a hot piece of hint! =)))

With this little helper, I can go for more soon...
Btw., what can I do if I have some dependency-collisions with different versions of installed and needed packages? Do I need a cross-compiler for that?

Oh and, how and where can I upload a .deb package for others to share it? Using the forum's attachment function doesn't work somehow...


perixx

---

### Post by Vadi on 2007-12-02
Look into Launchpad.net's PPA (Personal Package Archive) program.

---

### Post by perixx on 2007-12-02
Thx Vadi, for the hint - I'll do that anytime soon!

[COLOR="Blue"]Here's another good forum link on solving dependency problems along the hard compilation way:[/COLOR]
[http://ubuntuforums.org/showthread.php?t=624020&highlight=ubuntu+upload]("http://ubuntuforums.org/showthread.php?t=624020&highlight=ubuntu+upload")


perixx

---

### Post by perixx on 2008-01-09
I've been successful in compiling the Subversion/SVN (formerly CVS) developer's version in the meantime:

1. subversion has to be installed via Synaptic.

2. the following command at a terminal is needed:
```
svn co https://freedroid.svn.sourceforge.net/svnroot/freedroid ~/SVN/FD
```
It will 'checkout' (download) the latest source files from sourceforge to the stated folder: ~/SVN/FD (can be changed of course).

3. in the terminal, go to ~/SVN/FD (or folder where freedroidRPG-files reside) and type:
```
sh autogen.sh
``` now wait till it's finished. 
**NOTE:**You may need to install 'autotools', along with some other packages, via Synaptic; refer to this link here: [http://ubuntuforums.org/showpost.php?p=4071656&postcount=3]("http://ubuntuforums.org/showpost.php?p=4071656&postcount=3")

**For additionally required dependencies, see post #16 below!**

4. Next type this command and wait till it's done:
```
./configure
``` Afterwards you type and wait for
```
make
``` Should you get some weird warning message like mentioned here, simply ignore it:
[http://ubuntuforums.org/showthread.php?t=643548]("http://ubuntuforums.org/showthread.php?t=643548") 
**NOTE:** The game should already run by now, when going into the /src folder and running 'freedroidRPG'!

5. If you like to install it and create a .deb package, run
```
checkinstall
```
**Note:** if there are several different versions named, type the menu-number that refers to the stored versions and re-type it, so it only shows up once in the 'checkinstall' menu. Commence.

After finished, you should have a new .deb package availible, along with an installed new version of **freedroidRPG**! You should be able to find the binary in /usr/local/bin/freedroidRPG and make a starter to there, the actual game files reside in /usr/local/share/freedroidrpg.

Happy gaming / creating levels for the devels :)
perixx

---

### Post by stedevil on 2008-11-07
I posted this to the FDRPG maillist a while back, but I guess it cant hurt to repeat it here.

---
**Compile FreedroidRPG from source** 
on
Ubuntu 8.04 - Hardy Heron
Ubuntu 8.10 - Intrepid Ibex
Ubuntu 9.04 - Jaunty Jackalope
Ubuntu 9.10 - Karmic Koala
Ubuntu 10.04 - Lucid Lynx
Ubuntu 10.10 - Maverik Meerkat

(Should work on Xubuntu/Kubuntu/etc and probably most other versions too, do let us know)

**1)** First lets ensure you got the required Ubuntu packages for compiling FreedroidRPG.

Open a terminal window/console and:
```
sudo apt-get update
sudo apt-get install build-essential libsdl1.2-dev libjpeg62-dev zlib1g-dev libpng12-dev libsdl-image1.2-dev

```
For sound you also need
```
sudo apt-get install libsdl-mixer1.2-dev
```

**2)** Download latest sources (freedroidrpg-*.tar.bz2) and extract/unpack it.

[https://sourceforge.net/project/showfiles.php?group_id=54521&package_id=58238](https://sourceforge.net/project/showfiles.php?group_id=54521&package_id=58238)

**3)** **cd** to the folder you just extracted in a terminal window/console and
```
./configure
make
```

**4)** To play just
```
cd src/
./freedroidRPG
```

Instead of step 4, one can also **sudo make install** , but usually it's more convenient to just run from the source location since you might update often (especially if using the development version) and you dont risk problems with your package manager installing conflicting versions. The checkinstall tool mentioned in the post above mine works too.

---

For the development (SVN) version you would also in step 1 need to
```
sudo apt-get install subversion autoconf
```

Step 2) would instead be to download the source via SVN
```
svn co https://freedroid.svn.sourceforge.net/svnroot/freedroid path/to/folder/of/your/choise
```

and step 3 would need to have 
```
./autogen.sh
```
before ./configure

---

If you try this with other versions of Ubuntu than listed, please post your success including any modifications to above procedure you might have needed to make it work.

---

### Post by perixx on 2009-03-15
**A little off-topic, but related to use FD under Ubuntu (localized):**

Quoting from the README in your FD folder:

> Changing language in game will not work by default since Ubuntu does not ship with standard ISO locales, only UTF-8 versions. You will have to manually add them to make language selection work.
     
Procedure:

        1) In commandline write 
                ```
sudo nano /var/lib/locales/supported.d/local
```

        2) Add the locales you are interested in, 1 entry on each line, e.g.
                de_DE ISO-8859-15
                fr_FR ISO-8859-15
                sv_SE ISO-8859-15
                ru_RU.cp1251 cp1251
           and then exit with ctrl+x and yes to saving the changes.
Now run your game and choose your preferred language in the Options menu. 

**NOTE:** In the current version 0.12rc1, all localization support has been disabled. You'd need to manually compile a SVN revision prior to rev1819 or wait till this gets fixed again.

Happy gaming!

---

### Post by stedevil on 2009-03-15
> **perixx said:**
> **NOTE:** In the current version 0.12rc1, all localization support has been disabled. You'd need to manually compile a SVN revision prior to rev1819 or wait till this gets fixed again.


Slightly incorrect. 0.12rc1 DOES have localization (translations) included. They were however cut from 0.12 Final mainly because in general not being anywhere near release ready.

Once the translations get properly up to date we will add downloadable language packs. Before that, even while using SVN, the game experience will be quite lacking compared to English (the text stings missing will be falling back to original English, creating a mixed language situation, and the translated parts might in some cases be completely wrong due to changes in the game).

Assistance with translations is of course gladly accepted to speed up this process. :)

PS For having access to the half finished translations in latest SVN, recompile after removing the "// disabled-v0.12" at the start of the lines in src/vars.h for the language(s) you are interested in.

```

// disabled-v0.12	{ .code="fr_FR", .name="French", .font_class="", .encoding="ISO-8859-15" },
// disabled-v0.12	{ .code="de_DE", .name="Deutsch", .font_class="", .encoding="ISO-8859-15" },
// disabled-v0.12	{ .code="sv_SE", .name="Swedish", .font_class="", .encoding="ISO-8859-15" },
// disabled-v0.12	{ .code="ru_RU.cp1251", .name="Russian", .font_class=".cp1251", .encoding="cp1251" },

```

---

### Post by stinkyfishheadisred on 2009-08-27
For the latest version in the Ubuntu repositories (as of this post it was 0.10.3-3 for Ubuntu 8.04) you can always use the apt packages.  If you are running Ubuntu with Firefox, all you have to do is open [SIZE=3][apt:freedroidrpg](apt:freedroidrpg)[/SIZE] in the browser and it should start a graphical download process.

---

### Post by stedevil on 2009-08-28
Sadly FreedroidRPG is not backported, so older *buntu versions have really outdated versions. Even brand new versions are rarely up to date, due to the time lag introduced from the long winding process of:
New package in Debian -> Debian release freeze -> Debian stability test -> New package in Ubuntu -> Ubuntu release freeze -> Ubuntu stability test.

This creates a very stable and well tested system, but is very bad for a non system critical software like eg a game that is under heavy development.

---

### Post by pandanuma on 2010-07-28
great info here
note... I had to run configure twice before game would play

stedevil:  I think your instruction #3 should read 'make install' 


I kept the old version 0.12.1 and installed 0.13 and it may be conflicting with the new version,
(old version now deleted)
the old saved games from 0.12.1 will not load in 0.13...
even if they show up when trying to 'load existing hero'
...darn:(

Questions: 
  Where should I install the game?
  Right now it is in my /home/downloads/freedroidRPG directory.
  I am thinking it should go in /user/games?

---

### Post by stedevil on 2010-07-29
> **pandanuma said:**
> 
stedevil:  I think your instruction #3 should read 'make install' 


No, 'make install' comes (if at all) after 'make'. Check step 4 and the text after the step 4 code section.
'make' is what compiles the game, 'sudo make install' just moves the already compiled and playable gamefiles to a new location.

> 
I kept the old version 0.12.1 and installed 0.13 and it may be conflicting with the new version,

Yes, savegame compability between major versions can't be kept currently. Way too much is still being improved both in the engine as well as in the dialogs/events/world to make it possible (or even desired) to continue an old savegame in a new version.

> 
  Where should I install the game?
  Right now it is in my /home/downloads/freedroidRPG directory.
  I am thinking it should go in /user/games?

There have been many religious wars through decades now in the Linux community about exactly where which file should go. Funny thing is eg Gobo Linux proves it is all nonsense. My advice, put it where you think it should be, if it's in any case you yourself that will manage the updates of it (which on *buntu you likely will want to since the official *buntu packages are usually at least 1 version older than current release).

---

### Post by pandanuma on 2010-07-29
stedevil:
thank you for your patient answers
I should have read the intall and readme files first
Usually I am lazy and just install programs from the Ubuntu Software Centre application.

may I say that I detest this game...I just cannot turn it off :)
keep up the good work

---

### Post by stedevil on 2010-07-29
> **pandanuma said:**
> 
may I say that I detest this game...I just cannot turn it off :)


Muhaha! The path to world domination has begun! ;)

---

