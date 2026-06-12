---
title: "Playing your PS3 remotely on Ubuntu"
date: 2009-11-11
forum: Gaming &amp; Leisure
---

### Post by andersja on 2009-11-11
Open Remote Play is an open source tool that lets you play games or watch videos remotely from your PS3, by emulating being a PSP (which has remote play built in)

Currently only available for Windows and Mac:
[http://www.ps3-hacks.com/2009/05/22/open-remote-play-v12-beta-released/](http://www.ps3-hacks.com/2009/05/22/open-remote-play-v12-beta-released/)

Source code:
[http://code.google.com/p/open-rp/](http://code.google.com/p/open-rp/)

Is anyone aware of a Linux/Ubuntu port being progressed on this? I would guess it wouldn't be TOO hard, since the code is open and already cross-platform (Windows&Mac?)(famous last words?)

---

### Post by Digikid on 2009-11-11
Excellent idea!!!!!!!!!

---

### Post by andersja on 2009-11-12
I'm glad everybody thinks its a good idea. The next step, of course, is to find out if someone is already porting this or whether anyone would be interested in doing so? In the worst case it could be a case for WINE?

---

### Post by dashhacker on 2009-12-15
Hey guys...

Open Remote Play does run under Ubuntu.  You have to compile it from source as there is no binary package for it.  Feel free to make one.

If you do not want, or are unable to compile from source, you can run the Windows binary using WINE.  I've personally tested this with WINE v1.1.33.  You can download the latest WIN32 SVN snapshot from here:
[http://code.google.com/p/open-rp/wiki/Downloads?tm=2](http://code.google.com/p/open-rp/wiki/Downloads?tm=2)

To build from source, you require subversion (SVN), and either wget or curl installed.  Then run the following:

# svn checkout [http://open-rp.googlecode.com/svn/trunk/](http://open-rp.googlecode.com/svn/trunk/) open-rp
# cd open-rp
# make release

To run Open Remote Play:

# cd ORP-1.3-SVN-Linux
# ./orpui

Follow the instructions in the README:
[http://code.google.com/p/open-rp/source/browse/trunk/README](http://code.google.com/p/open-rp/source/browse/trunk/README)

You may also find the information in the FAQ useful:
[http://code.google.com/p/open-rp/wiki/FAQ](http://code.google.com/p/open-rp/wiki/FAQ)

Cheers,
Dashhacker

---

### Post by andersja on 2010-01-26
Dashhacker - thanks for the update. I will file a packaging request on Launchpad for this to be packaged & included.

---

### Post by andersja on 2010-01-26
FYI a formal packaging request on the bug tracker is here. Leave a comment if you think it's a great idea or if you have the patience & skill to make the .deb file...:

[https://bugs.launchpad.net/ubuntu/+bug/512755]("https://bugs.launchpad.net/ubuntu/+bug/512755")

---

### Post by juro on 2010-08-02
Hmm, I just tried this but I get this error:

```
/root/open-rp/packages.d/./work/root/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libpng12.la] Error 1
make[3]: Leaving directory `/root/open-rp/packages.d/work/libpng-1.2.37'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/open-rp/packages.d/work/libpng-1.2.37'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/root/open-rp/packages.d'
make: *** [all] Error 2
```

Is this still the only way to remote play from Ubuntu or is there a better way now?

---

### Post by jsngrimm on 2010-08-02
if someone can make a .deb there is this open source handheld coming out called OpenPandora wich runs linux. if it is achitecture specific it would need recompiled for ARM but it would be neat to remoteplay ps3 from a linux handheld. spec+info here [http://www.openpandora.org/](http://www.openpandora.org/) :)

---

