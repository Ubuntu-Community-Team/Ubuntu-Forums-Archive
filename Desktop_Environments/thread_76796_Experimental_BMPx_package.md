---
title: "Experimental BMPx package"
date: 2005-10-15
forum: Desktop Environments
---

### Post by shu on 2005-10-15
Hi all beep-media-player fans out there!

Just to let you know, I'm building bmpx package for breezy which is available here:

deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx) ./

You can expect new release once every few days, of course if there is something new released by bmpx team and it isn't totally broken. ;-)

shu

[SIZE="1"]If this post is in wrong forum or breaks any rules, do what you have to do ;-)[/SIZE]

---

### Post by gflores on 2005-10-15
Interesting, what's BMPx?

---

### Post by shu on 2005-10-15
[http://bmpx.berlios.de/w/index.php/FAQ#About](http://bmpx.berlios.de/w/index.php/FAQ#About)

---

### Post by Tomasz on 2005-10-15
Thanks, it seems to be working great! Good that the server is in the exact same city where I live :KS Pozdrowienia!

---

### Post by talkingwires on 2005-10-15
Ah, thank you. I could never manage to build my own. Extra props for creating a repository for it!

---

### Post by christooss on 2005-11-15
ahu what happend with 0.12.4 it doesn't start at my comp. So any of you have same problems

---

### Post by christooss on 2005-11-15
What happend with bmpy page it doesn't work for aout a week

---

### Post by christooss on 2005-11-15
They have moved to new location

[http://beep-media-player.org](http://beep-media-player.org)

There is a 0.12.6.1 version out

---

### Post by shu on 2005-11-15
Site has moved to [http://beep-media-player.org](http://beep-media-player.org). You're the first one who has problems with it. Try removing ~/.bmpx folder. Should work ;-)

Anyway I'll release 0.12.6.1 shortly.

---

### Post by christooss on 2005-11-15
I removed 4 files in .bmpx and now it works. I hate that I have to remove those files everytime I update.

Im looking forward to see 0.12.6.1 on my Ubuntu mashine

---

### Post by shu on 2005-11-15
0.12.6.1 should be available already.

---

### Post by christooss on 2005-11-16
:) Thanks for this. I upgrade it yesterday :) but.. there is already new version. 0.12.7

---

### Post by shu on 2005-11-16
There might be another 3 new versions before day ends. ;-)

---

### Post by christooss on 2005-11-16
True :)

---

### Post by Hairy_Palms on 2005-11-16
i must admit that im not greatly impressed with this, it seems like a slower loading version of bmp but with a library, and less stable.
but i have two question, how can i delete tracks from the library of bmpx ? and also how can i roll up bmpx like i always do with bmp?

---

### Post by christooss on 2005-11-19
Hehe shu. You have upgraded to 0.12.7 after 0.12.8 release :) There is to much development goin on in Bmpx

You cannot roll up bmpx.

---

### Post by christooss on 2005-11-19
Sorry I see now that package was build three days ago :)

---

### Post by shu on 2005-11-19
Well Hairy_Palms... bmpx is written from scratch. It has nothing to do with bmp and/or xmms except for that it can use winamp skins. If you're not satisfied with it, than stick with bmp, which is abandoned software, or xmms which is abandoned (or close..) too.

Bmpx uses gstreamer/xine for playing and it's getting better and better with every release. Sure there are lots of features lacking, and it's slow. It's slow because of the way database library is handled at this moment.

From my experience it _way_ better that bmp ever was and it is being developed very fast, what unfortunately cannot be said about any other player out there.

---

### Post by christooss on 2005-11-19
I agree with you shu.

I see in bmpx's future and I can see a bright and famous future.

shu do you know how bmpx chooses an xine/gstreamer. Is that "choice" made when compiling?

---

### Post by shu on 2005-11-19
As for my releasing speed christoos... I don't think that building every release makes sense, since as you know there are sometimes 3 releases on single day. Differences are mostly minor and it's best to let the 'latest & greatest' release to cool down a bit as it was with 0.12.6, which didn't work at all ;-)

Anyway if let's say 0.12.9 will be released on tuesday, then I will build it on tuesday/wednesday, so it will land on your desk around thursday (update notifier checks repositories once a day). 

0.12.8 is in my repository by the way. 

Answering your question: Backend can be chosen at build time. At this moment xine backend is preferred and supported option. For gstreamer backend you'll need development version of gstreamer (0.9.x) and I'm not sure if it will even compile properly right now. If/when gstreamer 0.10 (after it's released) will be backported to breezy, then I'll switch to gstreamer.

shu

---

### Post by christooss on 2005-12-06
Hello shu

Did you noticed that phase3 is "official" and that prefixes and paths are like at "phase 2"were

---

### Post by shu on 2005-12-07
Sure, but last time I did check out phase3 it wasn't very functional. I'll let them finish what they have to do and then release 0.13.

---

### Post by rwabel on 2006-01-09
@shu
do you know what this error message could be when doing "make"
```
grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive
make[4]: *** [libchroma.la] Error 1
```

I'm using dapper and not breezy

---

### Post by shu on 2006-01-09
Well, it says you don't have libXrender.la and it's probably right. ;) Check in package it is included and install it. There also might be something wrong with X packages at the moment in Dapper I guess.

---

### Post by rwabel on 2006-01-09
Yes I don't have that file. But I've installed libxrender stuff and I searched several times for the file on packages.ubuntu. no package contains that file. Here is the output:
```

usr/include/X11/extensions/Xrender.h                [libdevel/libxrender-dev]("http://packages.ubuntu.com/breezy/libdevel/libxrender-dev")
usr/lib/debug/usr/lib/libXrender.so.1.3.0            [libdevel/libxrender1-dbg]("http://packages.ubuntu.com/breezy/libdevel/libxrender1-dbg")
usr/lib/libXrender.a                        [libdevel/libxrender-dev]("http://packages.ubuntu.com/breezy/libdevel/libxrender-dev")
usr/lib/libXrender.so                        [libdevel/libxrender-dev]("http://packages.ubuntu.com/breezy/libdevel/libxrender-dev")
usr/lib/libXrender.so.1                        [libs/libxrender1]("http://packages.ubuntu.com/breezy/libs/libxrender1")
usr/lib/libXrender.so.1.3.0                    [libs/libxrender1]("http://packages.ubuntu.com/breezy/libs/libxrender1")
usr/lib/pkgconfig/xrender.pc                    [libdevel/libxrender-dev]("http://packages.ubuntu.com/breezy/libdevel/libxrender-dev")
usr/share/doc/libxrender-dev/changelog.Debian.gz        [libdevel/libxrender-dev]("http://packages.ubuntu.com/breezy/libdevel/libxrender-dev")
usr/share/doc/libxrender-dev/copyright                [libdevel/libxrender-dev]("http://packages.ubuntu.com/breezy/libdevel/libxrender-dev")
usr/share/doc/libxrender1-dbg/changelog.Debian.gz        [libdevel/libxrender1-dbg]("http://packages.ubuntu.com/breezy/libdevel/libxrender1-dbg")
usr/share/doc/libxrender1-dbg/copyright                [libdevel/libxrender1-dbg]("http://packages.ubuntu.com/breezy/libdevel/libxrender1-dbg")
usr/share/doc/libxrender1/changelog.Debian.gz            [libs/libxrender1]("http://packages.ubuntu.com/breezy/libs/libxrender1")
usr/share/doc/libxrender1/copyright                [libs/libxrender1]("http://packages.ubuntu.com/breezy/libs/libxrender1")
``` do you have that file? if yes, could you please attach it, maybe it works when I just copy it

o yes the funny thing is that the missing file is only in the dev package from hoary and even not in the one from breezy. Very wired

---

### Post by rwabel on 2006-01-09
the debian sid package has the file in the package. I could copy that one.

---

### Post by shu on 2006-01-09
Well, actually I don't have either, but bmpx compiles without it for me. Weird...

---

### Post by rwabel on 2006-01-09
did you als try the latest version: bmpx-2005-12-31-R1925?

---

### Post by shu on 2006-01-09
Sure. I even uploaded it to my repository, which wasn't very smart as this version is half-ready and mostly not-working. Maybe you should try my breezy package? It should work I think.

---

### Post by rwabel on 2006-01-09
strange thing :-)
I was using your debs on breezy, but since dapper has newer dbus stuff I get in dependency problems
```
dpkg: dependency problems prevent configuration of bmpx:
 bmpx depends on libdbus-1-1 (>= 0.36.2); however:
  Package libdbus-1-1 is not installed.
 bmpx depends on libdbus-glib-1-1 (>= 0.36.2); however:
  Package libdbus-glib-1-1 is not installed.
 bmpx depends on libtag1c2 (>= 1.3.1); however:
  Package libtag1c2 is not installed.
dpkg: error processing bmpx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bmpx
```

---

