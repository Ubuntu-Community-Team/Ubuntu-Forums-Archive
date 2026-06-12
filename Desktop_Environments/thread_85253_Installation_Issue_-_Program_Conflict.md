---
title: "Installation Issue - Program Conflict?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Ingla on 2005-11-02
I having some strange installation issues.

I wanted to install k3b (disk burning program). There were all kinds of dependency problems and when I tried to install the needed programs, some of them returned information saying they were not available but had been superceded by a new one. Installed those, but k3b was looking for the old file names and said it couldn't install. Then, it appeared in the menu...works and all! (I do seem to get "false alarm" error messages from time to time).

One strange point is that, while trying to install the needed programs, apt-get reported each time that was uninstalling k3b. So, after installing it, I told apt-get to install k3b...same thing...impossible to find depedency requirements. Even so it went in??!!

OK, whatever. It's there and it works. But now I tried to install Inkscape (graphics program) with Synaptic. It informs me it will have to uninstall k3b. Does this make sense? Can I not have both programs?

Any ideas or pointers on this?

Thanks very much.****

---

### Post by NewWithoutClue on 2005-11-02
i suggest you read up on APT's flaws, as well as it's real functions.
[http://www.debian.org/doc/manuals/apt-howto/index.en.html]("http://www.debian.org/doc/manuals/apt-howto/index.en.html")

w00t,
Paul.

---

### Post by NewWithoutClue on 2005-11-02
[What to do when Apt fails.]("http://www.linux.com/article.pl?sid=05/10/12/1952217")

Paul.

---

### Post by Ingla on 2005-11-02
Thanks very much for the replies. I hadn't realized this sort of thing could blow out the whole system![B]

QUESTIONS[/B]

_1.I ran dpkg --configure -a and got the following results:_

[COLOR="Red"]Setting up ronen-lyx-conf (0.0.1-1) ...
ln: `/usr/share/lyx/examples/splash.lyx': File exists
dpkg: error processing ronen-lyx-conf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdelibs4 (>= 4:3.3.2-6.1); however:
  Package kdelibs4 is not installed.
 k3b depends on libmusicbrainz4 (>= 2.1.1); however:
  Package libmusicbrainz4 is not installed.
 k3b depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ronen-lyx-conf
 k3b[/COLOR]

Apparently, this means I should get rid of k3b. That shouldn't be too hard.

But what do I do with this Lyx problem? Is ronen-lyx-conf a package, or just part of one?

What will happen if I try *dpkg --purge ronen-lyx-conf* (if it's not the name of the package)?

Would it be wiser to try to uninstall with Synaptic (which presumably knows what it is doing)?[U]

2. How exactly do I use -s or --dry-run?[/U]

Is it like this: sudo apt-get install -s (or --dry-run) PackageName ? Or is the syntax wrong?[U]

3. What happens if I type apt-get -f install or apt-get -f remove[/U]
without having recently installed anything? Does it find whatever needs to be dealt with or do I have to try an install first and then run these comands?

Any help appreciated.

Thanks very much.

---

### Post by GeneralZod on 2005-11-02
There's something horribly, horribly wrong here :)

Please post your /etc/apt/sources.list.

---

### Post by Ingla on 2005-11-02
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb [http://debian-hebrew.alioth.debian.org/debian/](http://debian-hebrew.alioth.debian.org/debian/) stable main
deb-src [http://debian-hebrew.alioth.debian.org/debian/](http://debian-hebrew.alioth.debian.org/debian/) stable main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse
deb [http://www.planet-moll.de/debian](http://www.planet-moll.de/debian) sarge main
deb [http://honk.physik.uni-konstanz.de/~wolfi/inkscape](http://honk.physik.uni-konstanz.de/~wolfi/inkscape) sarge/
deb-src [http://honk.physik.uni-konstanz.de/~wolfi/inkscape](http://honk.physik.uni-konstanz.de/~wolfi/inkscape) sarge/

##deb [http://security.debian.org/](http://security.debian.org/) stable/updates/updates main contrib non-free
##deb http:// secure-testing.debian.net/debian-secure-testing testing/secure-updates main contrib non-free
##deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) stable main  contrib non-free
##deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) testing main contrib non-free
##deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) unstable main contrib non-free

---

### Post by Ingla on 2005-11-02
By the way, the Debian repositories at the end of the source list were activated briefly at the suggestion of some post. However apt-get update returned error messages from them, so I took them back out of circulation.

---

### Post by Ingla on 2005-11-02
GeneralZod:

Hi.

I posted the source list, but you must have gotten busy in the meantime. Do you see anything I need to know about.

Meanwhile, I removed both programs with Synaptic. Now dpkg --configure -a comes back clean. I guess that means everything's OK? But now I don't have a CD burning program.

Please let me know about the source list.

Thanks

---

### Post by GeneralZod on 2005-11-02
[QUOTE=Ingla]GeneralZod:

Hi.

I posted the source list, but you must have gotten busy in the meantime. Do you see anything I need to know about.

Meanwhile, I removed both programs with Synaptic. Now dpkg --configure -a comes back clean. I guess that means everything's OK? But now I don't have a CD burning program.

Please let me know about the source list.

Thanks[/QUOTE]

Sorry - yes, I was a little busy.  I'd suggest temporarily commenting out all repositories but the Ubuntu ones, just in case.

---

### Post by Ingla on 2005-11-02
Thanks

---

