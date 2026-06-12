---
title: "FreeCiv"
date: 2007-10-31
forum: Game Specific Discussions
---

### Post by compiledkernel on 2007-10-31
Discuss here. All discussions fall under the general rules of the UGA Code.
No swearing, profanity, nudity or other such subversive images or communications.
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by Vadi on 2007-11-02
Can anyone get this to work?

There is no .deb, and the source code points to a non-existent INSTALL file :(

---

### Post by slickwilly on 2007-11-02
I just gave it a go myself, I think the problem, looking back over the output of autogen.sh is that I, and probably you also have a newer version of automake than what the game would like (1.6), this means the makefiles have screwed up syntax.
Using galternatives to set automake 1.6 as preferred version of automake to use might work, if you don't like digging about in makefiles.

If you get it work, post about it please, I've decided I can't really take the time off my machine today to compile this beast, as I have work to do and it will take a couple of hours :(


Slick

---

### Post by compiledkernel on 2007-11-02
I ran a normal 
./configure
make && make install 

and got it running, its only complaint was libgtk2.0-dev or the lack there of, not knowing which client to build.  "sudo apt-get install libgtk2.0-dev" fixed that and I was able to continue the configure and install.

---

### Post by slickwilly on 2007-11-02
I think he's talking about this message, which is what I got when I tried to build it:

make[7]: Nothing to be done for `all-am'

and also nothing to be done for 'all'

both of which are signs that it's trying to use the wrong version of automake, at least that's my understanding.


Slick

---

### Post by compiledkernel on 2007-11-02
Hmmm, I never ran into that actually.

---

### Post by slickwilly on 2007-11-02
Here are the relevant lines from autogen.sh output that I base my conclusion on, and galternatives does not work for changing automake, autogen finds the new version anyhow:

+ checking for autoconf >= 2.55 ... found 2.61, ok.
+ checking for autoheader >= 2.55 ... found 2.61, ok.
+ checking for automake >= 1.6 ... found 1.10, ok.
+ checking for aclocal >= 1.6 ... found 1.10, ok.
+ checking for xgettext >= 0.10.36 ... found 0.16.1, ok.
+ checking for msgfmt >= 0.10.36 ... found 0.16.1, ok.
+ creating acinclude.m4
+ running /usr/bin/aclocal-1.10 ...
acinclude.m4:972: the serial number must appear before any macro definition
acinclude.m4:2757: the serial number must appear before any macro definition
acinclude.m4:3160: the serial number must appear before any macro definition
acinclude.m4:3405: warning: ill-formed serial number `AM2', expecting a version string with only digits and dots
acinclude.m4:3774: the serial number must appear before any macro definition
acinclude.m4:3804: the serial number must appear before any macro definition
acinclude.m4:3816: warning: ill-formed serial number `AM1', expecting a version string with only digits and dots
acinclude.m4:3920: the serial number must appear before any macro definition
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT

As you can see it's finding newer versions than >= versions it is looking for, which would be the problem, it appears to me anyhow.

Slick

---

### Post by slickwilly on 2007-11-02
Oh and I suppose it's important to note that I was building 2.1.0 release, not any of the beta's or rc's, he did not say which version he was trying to build, important stuff, duh me for not thinking of it sooner, I have yet to have my third pot of coffee :(

Slick

---

### Post by compiledkernel on 2007-11-02
hrmmm....Nope, I havent run into it yet, and I just compiled the 2.1.0 source on a Feisty box here at work, and then reinstalled it on my laptop, just for kicks. Still not running into that issue.

---

### Post by slickwilly on 2007-11-02
Well just for giggles I downloaded the windows binary for the gtk client and gave it a run through WINE, wow!  15mins of wine fixme's followed by a page fault, lol :)

Well hopefully someone who can get this to compile will have mercy upon thoughs of us who cannot, and put together a binary package and chuck it up on Getdeb :)

I'll give another shot and getting this to compile later, too many jobs in the background right now, it would take aeons...

Slick

---

### Post by Vadi on 2007-11-02
I already asked getdeb to compile a package :)

It was pretty quick for me and didn't complain.

---

### Post by Vadi on 2007-11-03
Gotta love getdeb.net - ([click]("http://www.getdeb.net/app.php?name=FreeCiv"))

---

### Post by himasaram on 2007-11-05
> **Vadi said:**
> Can anyone get this to work?

There is no .deb, and the source code points to a non-existent INSTALL file :(

What do you mean by non-existent? It's located in the root directory of the source code. Are you sure you downloaded the tarball from sourceforge.net?

---

### Post by Vadi on 2007-11-05
There was an INSTALL.cygwin, but no INSTALL itself.

I installed it fine with the standard ./configure, make, and sudo make install.

---

### Post by Perfect Storm on 2007-11-06
A
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential
sudo aptitude install libgtk2.0-dev gettext libintl-perl bison bcp xlibs-dev x-dev libsdl1.2-dev libsdl-mixer1.2-dev libreadline5-dev


cd ~/Desktop
tar jxfv freeciv-2.1.0.tar.bz2
cd freeciv-2.1.0
./configure
make
sudo make install
```

should do it.

---

### Post by Loki.Satyr on 2008-06-01
Distibution: Ubuntu 8.04 Hardy
Package: freeciv-client-gtk
If the game does not start try:
```
civclient-gtk --Plugin sdl
```

If you get the console error message:
```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```
then run:
```
killall pulseaudio
civclient-gtk --Plugin sdl

```

---

