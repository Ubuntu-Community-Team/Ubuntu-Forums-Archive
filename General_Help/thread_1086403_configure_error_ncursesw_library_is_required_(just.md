---
title: "configure: error: ncursesw library is required (just curious)"
date: 2009-03-04
forum: General Help
---

### Post by Piraja on 2009-03-04
Dear all,

I decided to try and install ncmpcpp (mpd client) on 64-bit Ubuntu following the instructions found at the project's [website]("http://unkart.ovh.org/ncmpcpp/download.php"), using the git repository. These:

> To download live repository you'll need git system control version.

you have to execute the following command: 
```
git clone git://repo.or.cz/ncmpcpp.git 
```
then enter downloaded folder: 
```
cd ncmpcpp 
```
and regenerate configure script and makefiles by typing: 
```
./autogen.sh 
```
if it succeeded without errors, now it's time to run: 
```
./configure YOUR_CONFIGURE_OPTS (you can see them by typing ./configure --help)
make
make install 
```
However, if you want to install it from tarball, download and unpack it: 
```
tar pjvxf TARBALL_FILENAME 
```
then enter unpacked directory and type: 
```
./configure YOUR_CONFIGURE_OPTS
make
make install
``` 
congratulations, you have installed ncmpcpp :) 
Well, naturally I had to install quite a few packages (git-core, etc.) to get it done. But I didn't get any further than .autogen.sh, because:
> configure: error: ncursesw library is required

In Synaptic, I find:
> libncursesw5
Alright. No libncursesw in Intrepid 64-bit, but libncursesw5 instead.

This is really no big deal: I can always try another installation method or just stick with NCMPC which is a great MPD frontend already, without the few extra features in NCMPCPP. I'm just curious, an inquisitive n00b: is there a way to work around this?

---

### Post by Piraja on 2009-03-04
As an addition: How silly of me. The first thing to do would have been to check Launchpad for ncmpcpp, and indeed, I found M. Arnaud Guignard's [PPA]("https://launchpad.net/~aguignard/+archive/ppa"). You can get your NCMPCPP from there. Looks brilliant after a couple of minute's inspection. Thanks for reading, cheerio!

---

### Post by x33a on 2009-03-24
thanks man, was finding it difficult to find a repository :D

---

### Post by cirrusminora on 2009-04-16
Can you do this on Gutsy ? I'm on a 32 bit and can't seem to find any ncursesw library.Having libncursesw5 doesn't solve the problem ofcourse. Is there any repository for ncmpcpp itself or the ncursesw library ? I'm quite happy with ncmpc but would like to get those added features,as none of the hacks I found, worked.

---

### Post by lloyd_b on 2009-04-16
Did you guys install "libncursesw5-dev"?  When dealing with compiling software, if there is a "-dev" package for the thing it's asking for, be sure to install that (it'll generally auto-install the main library, if it's not installed already).

Lloyd B.

---

### Post by cirrusminora on 2009-04-16
Indeed installing the -dev package worked and I am able to get past autogen.sh. But on make, I get some errors involving an info.cpp file which I'm unable to locate. I get the following output :


kumar@kumar-laptop:~/Desktop/ncmpcpp-0.3.3$ make
make  all-recursive
make[1]: Entering directory `/home/kumar/Desktop/ncmpcpp-0.3.3'
Making all in src
make[2]: Entering directory `/home/kumar/Desktop/ncmpcpp-0.3.3/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..   -I/usr/include/ncursesw  -g -O2 -MT info.o -MD -MP -MF ".deps/info.Tpo" -c -o info.o info.cpp; \
        then mv -f ".deps/info.Tpo" ".deps/info.Po"; else rm -f ".deps/info.Tpo"; exit 1; fi
info.cpp: In member function &#8216;virtual void Info::Update()&#8217;:
info.cpp:80: error: &#8216;ArtistReady&#8217; was not declared in this scope
info.cpp:83: error: &#8216;Downloader&#8217; was not declared in this scope
info.cpp:85: error: type &#8216;<type error>&#8217; argument given to &#8216;delete&#8217;, expected pointer
info.cpp:87: error: &#8216;ArtistReady&#8217; was not declared in this scope
make[2]: *** [info.o] Error 1
make[2]: Leaving directory `/home/kumar/Desktop/ncmpcpp-0.3.3/src'
make[1]: *** [all-recursive] Error 1

And there it stops. I'm sorry for just parroting away the output like that but it would be nice if someone can pitch in.Thanks in advance. 

p.s : It would be real nice to get it working on my present gutsy because I don't have time to upgrade or change distro. Lately, though, gutsy repos seem to be totally out of sync with many current projects (gnome-do, pidgin, last.fm-rhythmbox etc.).

---

### Post by Daisuke_Aramaki on 2009-04-16
> **cirrusminora said:**
> Indeed installing the -dev package worked and I am able to get past autogen.sh. But on make, I get some errors involving an info.cpp file which I'm unable to locate. I get the following output :


kumar@kumar-laptop:~/Desktop/ncmpcpp-0.3.3$ make
make  all-recursive
make[1]: Entering directory `/home/kumar/Desktop/ncmpcpp-0.3.3'
Making all in src
make[2]: Entering directory `/home/kumar/Desktop/ncmpcpp-0.3.3/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..   -I/usr/include/ncursesw  -g -O2 -MT info.o -MD -MP -MF ".deps/info.Tpo" -c -o info.o info.cpp; \
        then mv -f ".deps/info.Tpo" ".deps/info.Po"; else rm -f ".deps/info.Tpo"; exit 1; fi
info.cpp: In member function ‘virtual void Info::Update()’:
info.cpp:80: error: ‘ArtistReady’ was not declared in this scope
info.cpp:83: error: ‘Downloader’ was not declared in this scope
info.cpp:85: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
info.cpp:87: error: ‘ArtistReady’ was not declared in this scope
make[2]: *** [info.o] Error 1
make[2]: Leaving directory `/home/kumar/Desktop/ncmpcpp-0.3.3/src'
make[1]: *** [all-recursive] Error 1

And there it stops. I'm sorry for just parroting away the output like that but it would be nice if someone can pitch in.Thanks in advance. 

p.s : It would be real nice to get it working on my present gutsy because I don't have time to upgrade or change distro. Lately, though, gutsy repos seem to be totally out of sync with many current projects (gnome-do, pidgin, last.fm-rhythmbox etc.).

didn't you use the configure script? and ncmpcpp0.3.3 is the latest release right? and doesn't it require libmpd latest alpha version?

---

### Post by cirrusminora on 2009-04-17
> **Daisuke_Aramaki said:**
> didn't you use the configure script? and ncmpcpp0.3.3 is the latest release right? and doesn't it require libmpd latest alpha version?

Yes, the configuration script does the same job as ./autogen.sh. 

ncmpcpp 0.3.3 is the latest, unstable release but not requiring libmpd alpha though : just the ncurses, tag and curl libraries. Check out the project homepage for this : [http://unkart.ovh.org/ncmpcpp/](http://unkart.ovh.org/ncmpcpp/) .

I went on to build ncmpcpp 0.3.2 from the tarball but again got stuck at the make stage. 


Output :

....goes on fine till :

../libtool: line 463: CDPATH: command not found
../libtool: line 1148: func_opt_split: command not found
libtool: Version mismatch error.  This is libtool 2.2.6, but the
libtool: definition of this LT_INIT comes from an older release.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.6
libtool: and run autoconf again.
make[2]: *** [ncmpcpp] Error 63
make[2]: Leaving directory `/home/kumar/Desktop/ncmpcpp-0.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kumar/Desktop/ncmpcpp-0.3.2'
make: *** [all] Error 2

How do I correct aclocal.m4 (which I can locate ; created during build ) with "macros from libtool " manually ? As you can see, I don't have much experience building from source. Any help appreciated !

---

### Post by cirrusminora on 2009-04-17
People, no one around ? I guess, with so many distros ahead of it already, its irrelevant to struggle, trying to adapt every darn latest version for gutsy.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **cirrusminora said:**
> People, no one around ? I guess, with so many distros ahead of it already, its irrelevant to struggle, trying to adapt every darn latest version for gutsy.

well when using single mode or consume mode, you do need libmpd alpha, and it is stated clearly in the website. now coming to your error, looks like there is a version error as far as libtool is concerned. verify what version of libtool you have on your system. If you use an older distro, obviously you will end up with some library mismatch. on the other hand if you use a source based distro, its not difficult to modify libraries.

---

### Post by Piraja on 2009-04-22
I had exactly the same issue as Cirrusminora with Intrepid, and am now having it in Jaunty [COLOR="Purple"]**[later addition: no problems any longer: see below]**[/COLOR]. For Intrepid, I could install NCMPC++ from Arnaud Guignard's PPA (merci monsieur!), but there seems to be no Jaunty repo for this app yet. In any case, the problem is not restricted to older versions of Ubuntu, such as Gutsy.

This really bugs me, because NCMPCPP is one of my most-used and most-liked applications! Please, somebody, package it for Jaunty, A.S.A.P.!...

... and a couple of minutes later, I realized my prayer was instantly heard & responded to:

> deb [http://ppa.launchpad.net/t.vetterlein/ppa/ubuntu](http://ppa.launchpad.net/t.vetterlein/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/t.vetterlein/ppa/ubuntu](http://ppa.launchpad.net/t.vetterlein/ppa/ubuntu) jaunty main

Thank you Tom Vetterlein!

---

### Post by cirrusminora on 2009-04-22
None for gutsy, eh ? Time to move on then, I guess. Having the same problem with too many applications.

---

