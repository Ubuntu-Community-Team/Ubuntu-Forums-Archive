---
title: "Need up-to-date repositories and help with installing .tar.bz2"
date: 2005-10-30
forum: Desktop Environments
---

### Post by dave164 on 2005-10-30
Whatever i do i cant seem to add the correct repositories for breezy

Is this correct?

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


On apt-get update i get the error message

"failed to fetch..." 
and
"couldn't stat source package..."


--------------------------


Also i am having trouble installing programs in .tar.gz and .tar.bz2, i can untar both of them but if i untar the .bz2 then the setup.sh is locked i believe, i am on the admin account and it says i dont have access..

I dont know how to install the .tar.gz after i have untard them, it says all you need to do in the INSTALL is 
./configure
make
make install

But that doesnt work... do i need to put anything after the make?

Thanks,
dave164

---

### Post by aysiu on 2005-10-30
I'd highly recommend you read this:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

It'll solve both your problems.

---

### Post by dave164 on 2005-10-30
Thanks alot, fixed the repositories.. just one more question

I read

"Installing from source, like the previous two methods, also does not resolve dependencies--you'll have to install those separately. The ./configure command may indeed tell you what dependencies you need but in a rather peculiar way; for example, it will often return with, say, a rather cryptic "gtk not found," in spite of the fact that the user has gtk installed! In fact, what is actually missing is the gtk development files, libgtkx.y-dev. In general, when it says "can't find library blah" and libary blah is already installed, it usually means that it can't find the blah development files, which can almost invariably be found and installed by searching synaptic for "blah dev."*"

I get this problem were it says:

Package gtk+-2.0 was not found in the pkg-conf ig search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to  the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adj usting the PKG_CONFIG_PATH environment variable if your libraries are in a nonst andard prefix so pkg-config can find them.


How do i fix this?

dave164

edit: Also i cant see there how to install .tar.bz2's

---

### Post by aysiu on 2005-10-30
[QUOTE=dave164]
edit: Also i cant see there how to install .tar.bz2's[/QUOTE] That *is* installing from source, so you were looking at the right part. Unfortunately, as my needs are meager (I install through Synaptic for almost everything), I don't really know how to deal with installing from source--that's why GeneralZod wrote most of that paragraph.

---

### Post by dave164 on 2005-10-30
Ok thanks, i guess i'll have to wait for someone else to help me with that one?

Ive managed to do the tar.bz2 now :)

Im just stuck on the gtk thing, do you have any idea how to install it?

---

### Post by aysiu on 2005-10-30
Probably no idea. Again, I don't really install from source. Just out of curiosity, what's the name of the package you're trying to install?

---

### Post by RAOF on 2005-10-30
For the gtk thing, you probably want to install the libgtk2.0-dev package.
In general, searching in Synaptic for the missing library (in this case "gtk") and looking for the -dev libraries (in this case, there's libgtk2.0-dev, along with libgtk2.0-bin, and a bunch of other libgtk-whatever things)

---

### Post by dave164 on 2005-10-30
Thanks ./configure works now, but when i do make, it just goes crazy with a laod more errors..

What are some other packages i might need?

Sorry for all the probably n00bish questions, new to all this

dave164

---

### Post by aysiu on 2005-10-30
I don't know if I can help, but it's always better to copy and paste the errors here than to just say you got a load of errors.

---

### Post by dave164 on 2005-10-30
callbacks.c:9:18: error: pcap.h: No such file or directory
In file included from callbacks.c:24:
PacketSource.h:153: error: syntax error before ‘pcap_t’
PacketSource.h:153: warning: no semicolon at end of struct or union
PacketSource.h:154: warning: data definition has no type or storage class
PacketSource.h:163: error: syntax error before ‘}’ token
PacketSource.h:163: warning: data definition has no type or storage class
PacketSource.h:173: error: syntax error before ‘*’ token
PacketSource.h:174: warning: data definition has no type or storage class
PacketSource.h:175: error: syntax error before ‘*’ token
PacketSource.h:176: error: syntax error before ‘*’ token
PacketSource.h:176: warning: data definition has no type or storage class
PacketSource.h:177: error: syntax error before ‘*’ token
PacketSource.h:178: error: syntax error before ‘*’ token
PacketSource.h:179: error: syntax error before ‘*’ token
In file included from bssidlist.h:35,
                 from display.h:23,
                 from callbacks.c:29:
capture.h:49: error: syntax error before ‘PacketSource’
capture.h:49: warning: no semicolon at end of struct or union
capture.h:51: error: syntax error before ‘}’ token
capture.h:51: warning: data definition has no type or storage class
callbacks.c:79: error: ‘PCAP_ERRBUF_SIZE’ undeclared here (not in a function)
callbacks.c: In function ‘on_Start_clicked’:
callbacks.c:368: error: ‘ca’ undeclared (first use in this function)
callbacks.c:368: error: (Each undeclared identifier is reported only once
callbacks.c:368: error: for each function it appears in.)
callbacks.c:378: error: syntax error before ‘)’ token
callbacks.c: In function ‘on_pcap_ok_clicked’:
callbacks.c:670: error: ‘ca’ undeclared (first use in this function)
callbacks.c:670: error: syntax error before ‘)’ token


Cheers,
dave164

---

