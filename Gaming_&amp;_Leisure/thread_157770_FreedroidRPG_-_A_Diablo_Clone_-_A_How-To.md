---
title: "FreedroidRPG - A Diablo Clone - A How-To"
date: 2006-04-09
forum: Gaming &amp; Leisure
---

### Post by mike998 on 2006-04-09
Well, I finally got around to installing FreedroidRPG...
If you are interested in WHAT FreedroidRPG is follow [THIS LINK]("http://wiki.linuxquestions.org/wiki/FreedroidRPG")
Here's my how-to.

First install the required libraries.
```
sudo apt-get install build-essential libsdl1.2-dev libjpeg62-dev zlibg-dev libpng12-dev libsdl-image1.2-dev libpng12-dev libsdl-image1.2-dev libsdl-net1.2-dev libvorbis-dev libsdl-mixer1.2-dev libgtk1.2-dev libgtk2.0-dev
```

I am not sure whether or not it's supposed to be libgtk1.2 or 2.0...  So I installed both.

Dowload the source from [http://prdownloads.sourceforge.net/freedroid/freedroidRPG-0.9.13-rc3.tar.bz2?download]("http://http://prdownloads.sourceforge.net/freedroid/freedroidRPG-0.9.13-rc3.tar.bz2?download")
 (Choose your nearest mirror)

Move to your download directory and then unzip/untar the file with 
```
tar -xjvvf freedroidrpg-0.9.13.tar.bz2
```

Move into the correct directory
```
cd freedroidrpg-0.9.13/
```

Configure and install the program with
```
./configure && make
sudo make install

```

And although I haven't tested it, this pasted into a 
```
sudo gedit /usr/share/applications/freedroidrpg.desktop
```
SHOULD give the start menu entry for FreedroidRPG.  I prefer the command line, so I don't really care about this portion.  If someone can correct this, then please do!
```

[Desktop Entry] 
Name=FreedroidRPG
Comment=FreedroidRPG - A Diablo/Freedroid fusion
Exec=/usr/local/bin/freedroidRPG
Icon=/usr/local/share/freedroidrpg/graphics/paraicon.bmp
Terminal=false
Type=Application
Categories=Application;Games;

```

Alternately, just type 
```
freedroidRPG
```
at the terminal and enjoy!

Any comments?  Questions?

Disclaimer: this worked for me.  Your Milage May Vary.

EDIT : For some reason the game crashes sometimes in town.  No reason, it looks like a normal game end...  Any help would be appreciated.

EDIT : The crashes are in town and I can't get a reply from any of the devs on this project about these.

---

### Post by Denta on 2006-04-10
Is it fun to play? Looks to good to be true...

---

### Post by mike998 on 2006-04-10
[QUOTE=Denta]Is it fun to play? Looks to good to be true...[/QUOTE]

Yep it is fun to play.  Very Diablo-like.
I haven't figured out how the sub-game works (The ability to take over other 'droids).

As I mentioned in my post, the only problem I have noticed is that the game crashes once in a while and at random.  I haven't figured out why yet.

---

### Post by BeatBoxRocker on 2006-04-10
Thanks for the info mike998, it looks really good. I was looking for a game like diablo but i havent heard of this game before in any linx games web page ;)

Saludos!

---

### Post by mike998 on 2006-04-11
I'd found the game a couple of years ago and played the windows version.
I loved Diablo (I and II) but to get them working on Linux is a pain.  This seems to fulfil my Diablo requirements!

---

### Post by charlieg on 2006-04-12
Call me old fashioned or lacking imagination, but running around as a penguin just does not really grab my attention like a classic RPG scenario (BG or Diablo).  This is why I have high hopes for [Scourge](http://scourge.sourceforge.net).

---

### Post by Perfect Storm on 2006-04-12
Looks good. Good found!
But as charlieg says I agree with. I'm one of those who likes to identify/"playing" a character and it's bit hard to me "being" a penguin :)

---

### Post by mike998 on 2006-04-12
I must admit, it's hard to "be" the penguin...

I'm starting to get very annoyed at the crashes in this game.  I have asked in the IRC channel that the developer has on his webpage and got no reply.  I will mail them tonight and find out if the crashes are anything that can be prevented.

Scourge looks cool - I think I will give it a try tonight...  I don't hold out much hope as my laptop's graphics card is pretty crappy.

---

### Post by Skikkles on 2006-09-18
Sorry to bother you all...

I was trying to do this install, and maybe I'm just too new at this Linux thing but everytime I try I have issues with it.

 Couldn't find package zlibg-dev

I keep getting this and when I try to run the install && make command it tells me that it cannot find the Make.IN file in the src.... (can't remember what it said exactly)

Any insight to this would be greatly appreciated.

---

### Post by Perfect Storm on 2006-09-18
How's your sourcelist looks like?

```
cat /etc/apt/sources.list
```

---

### Post by Skikkles on 2006-09-18
Here it is...doesn't make much sense to me.


deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Perfect Storm on 2006-09-18
Looks something is missing.

Back up your soucelist and use mine instead:

```
sudo nano /etc/apt/sources.list
```

backup your current list then clear the sourcelist and add this instead:
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror.ubuntulinux.nl dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

## dapper-commercial by canonical
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Save (ctrl +o) and exit (ctrl + x) it.

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by darkazurka on 2010-05-06
latest version: freedroidRPG 0.13 is out, although I've now installed version from Lucid 0.12.1-1.

[http://freedroid.sourceforge.net/download.php](http://freedroid.sourceforge.net/download.php)

---

