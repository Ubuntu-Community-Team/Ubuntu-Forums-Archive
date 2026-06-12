---
title: "Problem: Installing eggdrop1.6.18 + SSL Patch"
date: 2006-09-02
forum: Desktop Environments
---

### Post by SeQual on 2006-09-02
Hello,

Will put my problem in steps for easier and to the point reading.

1. First I installed the following, tcl8.4.13. As its needed to be able to install the eggdrop.

cd tcl8.4.13/unix
configure
make
make test
make install 
[COLOR="SeaGreen"]Done.[/COLOR]

2. Downloaded eggdrop1.6.18, unpacked it.

```
elite@no1:/downloads$ ls
eggdrop1.6.18  eggdrop-1.6.18-ssl.patch  eggdrop1.6.18.tar.gz  tcl8.4.13
```
[COLOR="SeaGreen"]Done.[/COLOR]

3. Copy the patch to eggdrop dir, apply patch.

```
elite@no1:/downloads$ sudo cp eggdrop-1.6.18-ssl.patch /downloads/eggdrop1.6.18
elite@no1:/downloads$ cd eggdrop1.6.18/
elite@no1:/downloads/eggdrop1.6.18$ ls
aclocal.m4  config.h.in  configure.ac  COPYING           doc                       eggdrop.conf  help     language  Makefile     misc  README   src
ChangeLog   configure    CONTENTS      disabled_modules  eggdrop-1.6.18-ssl.patch  FEATURES      INSTALL  logs      Makefile.in  NEWS  scripts  text

elite@no1:/downloads/eggdrop1.6.18$ sudo patch -p0 < eggdrop-1.6.18-ssl.patch
patching file Makefile.in
patching file aclocal.m4
patching file config.h.in
patching file configure
patching file configure.ac
patching file src/Makefile.in
patching file src/dcc.c
patching file src/dccutil.c
patching file src/eggdrop.h
patching file src/main.c
patching file src/md5/md5.h
patching file src/md5/md5c.c
patching file src/mod/compress.mod/compress.c
patching file src/mod/irc.mod/chan.c
patching file src/mod/irc.mod/irc.c
patching file src/mod/irc.mod/irc.h
patching file src/mod/irc.mod/mode.c
patching file src/mod/module.h
patching file src/mod/server.mod/servmsg.c
patching file src/modules.c
patching file src/net.c
patching file src/net.h
patching file src/patch.h
patching file src/tcl.c
patching file src/tclmisc.c

```

4. Configure eggdrop

```

elite@no1:/downloads/eggdrop1.6.18$ sudo ./configure

This is Eggdrop's GNU configure script.
It's going to run a bunch of tests to hopefully make your compile
work without much twiddling.

checking for gcc... gcc
.
. (configuring area...)
.

```

At the end of configuration
```
checking types of arguments for select... int,fd_set *,struct timeval *
checking whether to include SSL support... will try to find
checking for SSL_accept in -lssl... no
configure: error: OpenSSL was not found. Please supply a pathname to OpenSSL
elite@no1:/downloads/eggdrop1.6.18$

```

OpenSSL is installed but can't seem to fix it to make the eggdrop find the files, I know had this prob before in 5.10.

Was using a server edition, back then I did this to make the eggdrop find it:

```
    * apt-get install openssl
    * cp -r /usr/local/ssl/include/openssl/ /usr/include/ #Otherwise the eggdrop won’t find the files.
    * cp /usr/local/ssl/lib/libcrypto.a /usr/lib/;cp /usr/local/ssl/lib/libssl.a /usr/lib/
```

First time I use a desktop version, in desktop openssl is pre-installed it seems =D> .


Anyone have some advice of how to fix the openssl problem? Tnx in advance.

---

### Post by SeQual on 2006-09-03
Haven't solved this issue yet.

Tried re-installing openssl, in case it wasn't fully there. but seems it is. just don't find all files of it.


Anyone tried installing latest eggdrop with ssl yet?

---

### Post by SeQual on 2006-09-04
Can someone else test this on his machine?


Don't forget to patch the eggdrop source with the SSL files first, otherwise u won't get the error of course after doing ./configure


In short the steps that need to be done to install the whole eggdrop with ssl

```

Download eggdrop source from http://www.egghelp.org/

You also need the ssl-patch for your version of eggdrop from same place as above.

In my example I will show you with version 1.6.18;

- Download the source files:
  wget ftp://ftp.eggheads.org/pub/eggdrop/source/1.6/eggdrop1.6.18.tar.bz2
  (or ftp://ftp.eggheads.org/pub/eggdrop/source/1.6/eggdrop1.6.18.tar.gz if you want the gzipped version)

  wget http://www.egghelp.org/files/patches/eggdrop-1.6.18-ssl.patch.gz

- Extract the files:
  tar -jxvf eggdrop1.6.18.tar.bz2
  ( or tar -zxvf eggdrop1.6.18.tar.gz if you took the gzipped version)

  gzip -d eggdrop-1.6.18-ssl.patch.gz

- Patch and compile the sources
  cd eggdrop1.6.18
  patch -p1 < ../eggdrop-1.6.18-ssl.patch
(if above gives errors, do:   patch -p0 < ../eggdrop-1.6.18-ssl.patch )
  ./configure
  make config
  make
  make install

```

Thanks :-k

---

### Post by f00buntu on 2006-09-05
I have no experience installing eggdrop but reading your post i think you need libssl-dev

sudo apt-get install libssl-dev

hope it helps

---

### Post by not applicable on 2006-09-05
A friend of a friend directed me to this post due to the fact they are suffering from this same issue.  I've sucessfully implimented eggdrop+ssl on a few distro's without issue, but cannot seem to help them getting theirs working properly.  And unfortunately I don't have the extra hardware atm to do a ubuntu install so I can work on this problem directly.

I'm shocked this thread has no replies as of yet (3 days old).  I'm even more shocked that I visited the ubuntu channel in freenode and was able to receive no help after posting the issue several times.  I'm not trying to be rude or anything but I do recommend to many people trying *nix as an alternative, one of the biggest points I stress is the fact that their is help available all over the place.

All I can say is to possibly try the ubuntu irc channel and hopefully you'll make out better then I did.

Best of luck,  I'll be following this thread.  Hope some input will be given to get this guy going so I in turn can help my friends buddy as well

---

### Post by not applicable on 2006-09-05
f00buntu, thanks for replying.  Must have come in while I was still typing mine.  I'll also have my friend check this as well and will post their findings.

Thx for taking the time :)

---

### Post by not applicable on 2006-09-05
foobuntu, got ahold of my buddy with the ubuntu rig.  He did as you suggested and told me it "seems" to have worked.  It's now compiling with no errors, at least none up to this point.  Thanks and will keep you informed.

would also like to say that I'm a member of a private forum of only like 45-50 people max.  Threads in that tiny community and questions in our irc channel seem to get a much better response than a community as large as this?  
I think it's sad someone had to wait as long as this guy to receive any help.  Not to mention that as I stated previously I also was inquiring about this for another guy and received no help what so ever in the irc channel.  This will definately be something I'll mention to anyone thinking of using ubuntu.

Thanks for your time Foobuntu, as I said your fix seemed to work but will post again when I know for certain.

---

### Post by not applicable on 2006-09-11
sorry for the delay in confirmation as to whether or not the suggested fix worked.  Been rather busy as of late and not much time.

Well, regrettably adding the package you mentioned didn't solve the issue f00buntu, but thanks so much for the response.  I was hoping by now their might have been more replies to the thread, but apparently that was wishful thinking.

I must say, and I'm in no way trying to start a flame war.  But with the lack of response in both here and in the irc channel I've personally decided that I will never try this distro again.  It's rather sad really, I did check out the live disc at one point but was looking for more of a server OS so decided to use slackware.  I've since moved on to bigger and better things and currently run FreeBSD.  Neither of these distro's did I have this much trouble getting a response to a question.  I'm assuming by this either the community feels the questions isn't worth their time in responding to.  Or is to complex and nobody knows, end result tho is the same the poor guy that started this thread and my friends buddy get no help.

I've only posted here a few times, but I've also noticed that the forum loads VERY slowly, sometimes even causing a page cannot be displayed due to a timeout.  I'm adressing these points not to bash your community or forum, but simply as a way to point out things I see as barriers which could potentially stop people from trying Ubuntu.  I hope these points will make an impact and get these issues resolved, but it's been quite a long time since this post was originally made and other then myself and the gentlemen that started the thread, only one other person has replied so I doubt this reply will even be noticed.

Perhaps it's best if I start a new thread about this to better call attention to what I feel are "problem areas".  It does make me wonder tho.  

thanks,
concerned open source user

---

### Post by jazzykay on 2006-09-24
Hello, 

I got this to work. 

Step 1: Download the code for eggdrop and patch it with ssl
This site has a good set of instructions on what to do:
[http://remus.oru.se/tsub/eggdrop-ssl/]("http://remus.oru.se/tsub/eggdrop-ssl/")

The only issue I had was patching when following the instructions off this site:
Patch and compile the sources
  cd eggdrop1.6.18
  patch -p1 < ../eggdrop-1.6.18-ssl.patch --> should be patch -p0 < eggdrop-1.6.18-ssl.patch

Step 2: Open SSL issues when compiling. 
I had openssl but ./configure still failed. 
I followed f00buntu and did the sudo apt-get install libssl-dev
I then opened another shell and did configure again. 

Step 3: TCL issues
The tcl that i downloaded with synaptic was not cutting it. The eggdrop configuration script was asking for libraries and headers. 
So I followed the instructions from this site 
[http://openacs.org/xowiki/en/tcl-install]("http://openacs.org/xowiki/en/tcl-install")

"Install Tcl

Get TCL 8.4 (or higher). Download and install TCL 8.4 from source.

If you have not installed TCL already, download the latest TCL version from Sourceforge or [http://www.tcl.tk/software/tcltk/downloadnow84.html](http://www.tcl.tk/software/tcltk/downloadnow84.html)

Remember that you have to be logged in as root to issue the following commands.

cd /usr/local/src
wget [http://heanet.dl.sourceforge.net/sourceforge/tcl/tcl8.4.13-src.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/tcl/tcl8.4.13-src.tar.gz)
tar xfz tcl8.4.13-src.tar.gz
cd tcl8.4.13/unix
./configure --enable-threads
make install
"

I opened a new shell after this so environment variables were sourced. 

Everything worked smoothly from here on out. I kept opening new shell sessions so my variables would get sourced properly. 

Make sure eggdrop.conf is configured properly.

Hope that helps. 

jazzykay

---

