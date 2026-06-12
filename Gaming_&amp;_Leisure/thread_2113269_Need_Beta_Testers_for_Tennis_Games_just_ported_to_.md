---
title: "Need Beta Testers for Tennis Games just ported to Linux !"
date: 2013-02-06
forum: Gaming &amp; Leisure
---

### Post by ManuTOO on 2013-02-06
Hello,

I'm the author of the tennis games "Tennis Elbow 2013" and "Tennis Elbow Manager", available so far on Windows & Mac OSX. I just ported them to Linux, and I'd be glad if some Linux users could tell me if they work correctly on their setup.

TE2013 Demo : [http://www.managames.com/download.php?TE2013-Linux_BetaU.gz]("http://www.managames.com/download.php?TE2013-Linux_BetaU.zip")
TeManager Demo : [http://www.managames.com/download.php?TEM-Linux_BetaU.gz](http://www.managames.com/download.php?TEM-Linux_BetaU.gz)

In TE2013, you play tennis, and in TeManager, you're a tennis coach managing your player(s).

Please report any glitch, bug or crash you may experience. Post the System.log from the game folder if possible.
It's  working with Ubuntu 12.04, so I guess it should work with other Fedora  distribs and hopefully most of other popular Linux distribs ; don't  hesitate to report if it's working well on your distrib..!

So far, I noticed these 2 bugs :
- sound is very delayed, about half a second
- mouse doesn't work in fullscreen

I hope that both are because I'm running Ubuntu within VmWare.

Right now, it's still missing the config tool to select your language ; I already created it but still didn't put it in the package.

Thanks in advance for any report ! :)

PS: if you buy the game, just copy your Key.txt into your game folder (I still didn't create the email template for Linux Key :redface: ).

[IMG]http://static.managames.com/Images/TennisElbow/TE2013_IndieDB.jpg[/IMG]

---

### Post by Perfect Storm on 2013-02-08
Stick'ed for a period.

---

### Post by DirtyPC on 2013-02-09
Whats the price for the games?

---

### Post by ManuTOO on 2013-02-09
[B][[COLOR=#DD4814]Artificial Intelligence,[/COLOR]]("http://ubuntuforums.org/member.php?u=19")
[/B] thanks ![B]

[harrylucas1]("http://ubuntuforums.org/member.php?u=1174686")[/B],
US$24.95 for each game ; US$37.42 both games together (ie: 50% off the 2nd game, whenever you buy it).

---

### Post by ManuTOO on 2013-02-13
I just updated the Betas : the games were requiring you to have installed SDL and all its dependencies to work ; now, all the required Libs are loaded from the subfolder "SdlLib" , or at least hopefully so ; I successfully tested on a naked Ubuntu 12.04, but maybe other distrib will miss some libs ; thanks to let me know if it's the case on your Linux.

---

### Post by Bölvaður on 2013-02-13
For Tennis Elbow 2013

```
./TennisElbow2013: error while loading shared libraries: libtiff.so.4: cannot open shared object file: No such file or directory

```

Ubuntu 12.04 uses libtiff5 (libtiff.so.5)

After installing libtiff4 it seems to be working for normal play.

Fiddling with the resolution results in a crash if I do this:
Windowed mode, on 1024×768
Change to Full screen mode, still on 1024×768
Change to 1280×1024, crash
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  150 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x2b2
  Serial number of failed request:  342
  Current serial number in output stream:  344

```

If you start in full screen with 1280×1024 (from startup of the game) and then do the following:
Change fullscreen to windowed,
Change windowed to fullscreen,
Change from higher resolution to lower,
Change from lower resolution to higher.

Then you should see artifacts on the "newly revealed" part of the screen. Then you will be forced to press escape button few times to close the program and then start it up again. It obviously works then as it is the change going from lower to higher resolution that seems to be doing this.

---

### Post by ManuTOO on 2013-02-14
**Bölvaður**,
thanks for your report !
I don't have libtiff5 on my Ubuntu 12.04 (both fresh one & up-to-date one) ; I'll put libtiff4 in the SdlLib folder anyway with next package, it can't hurt (I hope so! :P ).

I couldn't reproduce both of your video bugs ; I can get the same error message when I try to set the video mode to an higher resolution than the max possible, though.
Would it be possible for these issues to be linked to your display drivers ?

Could you tell me if the mouse was working well in full screen ? And if the sound was delayed or not ?

---

### Post by ManuTOO on 2013-02-20
I updated the packages again, added a couple of libs, and now the games auto-detect the language on 1st start, and let you change the language from the "Misc Options" menu.

Website has been updated as well, so these are Release Candidates, hopefully working well... ;)

---

### Post by andrew.46 on 2013-02-20
Nice! I have only tried TennisElbow2013 so far under Slackware -current. Runs nicely, there is a terminal message on startup:

```

./TennisElbow2013: /usr/lib/libcurl.so.4: no version information available (required by ./TennisElbow2013)

```

which does not affect actual gameplay...

---

### Post by ManuTOO on 2013-02-20
**andrew.46**,
thanks for your report !

I did a quick search, and it may mean you don't have CURL installed on your system.
Could you try this command to see if it output anything ?
```
curl-config --version
```(I found this in this topic : [http://ubuntuforums.org/showthread.php?t=1156845](http://ubuntuforums.org/showthread.php?t=1156845) ;) )

CURL is only used to contact the server to check for new version, so it's not much needed anyway ; and as it's done on 1st launch, I guess either if it's missing or a wrong lib version, it will likely never prevent the game to start.

---

### Post by andrew.46 on 2013-02-20
Curl is there:

```

andrew@skamandros~$ curl-config --version
libcurl 7.29.0

```

Actually in 2 places as I am running the multi-lib version of 64bit Slackware:

```

root@skamandros/home/andrew# find /usr -iname libcurl.so.4
/usr/lib/libcurl.so.4
/usr/lib64/libcurl.so.4

```

---

### Post by ManuTOO on 2013-02-20
I just checked and I have Curl 7.22.0 with Ubuntu 12.04 ; that's not too different from 7.29, so I have no idea why you got that error message... But anyway, it's working that's the most important ! ;)

---

