---
title: "Kaffeine 0.7 is crashing"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Jonathan2007 on 2005-10-18
This is a copy of [this]("http://ubuntuforums.org/showthread.php?t=67503&highlight=kaffeine+crashes") thread from the Ubuntu mailing list forum. I am also experiencing frequent Kaffeine crashes just like what happened in 0.6 (where we had to get that fixed deb package). I thought more people might see it over here and maybe we could get a solution.

> Am I the only one experiencing crashes with kaffeine v0.7 under breezy
with the latest updates applied?

When I open up the application and open a file it plays it fine. When
the playback is done, and I try to open an other file, as soon as I
click the 'Open File' option, it crashes on me. KDE's crash handler
gives me no useful information.

Any idea? It does not seem to me to depend on the codec/container
format, as it does it with all.

---

### Post by Pumpino on 2005-10-19
Exactly the same thing here!  As soon as I click on Open, the program crashes.  Did they even test it before they released it?!  Licq doesn't even connect to the icq network either.  The bugs in these programs are apparent after less than 2 mins of use.  Sheesh!

---

### Post by mcz on 2005-10-19
[QUOTE=Pumpino]The bugs in these programs are apparent after less than 2 mins of use.  Sheesh![/QUOTE]
It.s not a problem of the program itself.
I use Kaffeine 0.7 without any (I mean any=nothing) problem in Gentoo, Suse, Mandrake and Fedora.
I will try it also with Debian very soon.

mcz :p

---

### Post by Jonathan2007 on 2005-10-19
Well I think he is meaning don't they test it in Kubuntu at all before it is released? And I don't think I am being too harsh because this exact bug happened with kaffeine 0.6 and everyone had the problem and I think it was a pretty big deal so I would have thought they would have made sure it didn't happen again. :rolleyes:

---

### Post by Pumpino on 2005-10-19
I've given Kaffeine the arse and I'm using VLC now.  Totem is good, but I think I prefer VLC for the moment. :)

---

### Post by gingermark on 2005-10-19
Having crashes with 0.7, same as 0.6, but someone posted a link to a deb file for a modified version which I ran under hoary which was perfect - never had a crash with it.

I'll have to have a search for it, assuming it would work in breezy??

EDIT: Found it - as detailed here: [http://www.ubuntuforums.org/showthread.php?t=27670](http://www.ubuntuforums.org/showthread.php?t=27670)

This version was great - will it work in Breezy? I'm aware that Kafeine moved over to Gstreamer... Still, would there be any reasons not to give it a go?

EDIT AGAIN: I though "what the hell" and tried it - got the following errors:

Preparing to replace kaffeine 0.7-0ubuntu4 (using kaffeine_0.6-1_i386.deb) ...
Unpacking replacement kaffeine ...
dpkg: error processing kaffeine_0.6-1_i386.deb (--install):
 trying to overwrite `/usr/share/services/kaffeine_part.desktop', which is also in package kaffeine-xine
dpkg-deb: subprocess paste killed by signal (Broken pipe)

So, probably a bad idea then? :D

EDIT ONE LAST TIME: I noticed in that thread the person who made the package said:

[QUOTE=Zakalwe]All I did was dpkg-buildpackage the latest sarge source package on kubuntu :) Zack Cerza ( The debian package maintainer) is the one who did the real work here so thanks are due to him.[/QUOTE]

Maybe someone could do something similar in Breezy? And by someone I mean not me, unless that is someone wants to give me instructions!

---

### Post by Jonathan2007 on 2005-10-23
Anyone find a solution to this? And how come only some of us are having this weird crashing? Everyone with Kaffeine 0.6 in Hoary had the problem...

---

### Post by DeeZiD on 2005-10-23
I've got a fix for you:
deb [http://ubuntu.czessi.net/](http://ubuntu.czessi.net/) breezy stable stable-updates 
deb [http://ubuntu.czessi.net/](http://ubuntu.czessi.net/) breezy testing testing-updates 
deb [http://ubuntu.czessi.net/](http://ubuntu.czessi.net/) breezy unstable unstable-updates 

There are many replacements and new applications in this repository, mainly for KDE.
Have fun ! :D 

Thread from the ubuntu-community in germany:
[http://www.ubuntuusers.de/viewforum.php?f=26](http://www.ubuntuusers.de/viewforum.php?f=26)


Dennis

---

### Post by DeeZiD on 2005-10-23
Oops, he removed the kaffeine-package a week ago
here is a link:
[http://www.ubuntuusers.de/viewtopic.php?t=12704](http://www.ubuntuusers.de/viewtopic.php?t=12704)


Dennis

---

### Post by Jonathan2007 on 2005-10-23
So I downloaded the 0.7.1 package off that German Ubuntu site. It was hosted on rapidshare and was a .tar.bz2. But inside was 3 .debs. They included kaffeine, kaffeine-xine, and kaffeine-gstreamer. I decided to uninstall my old Kaffeine before trying to install the new one. I got the old one uninstalled and went to install the new one. It gave me a dependency error saying it need the xine and gstreamer packages. I then tried to install both of those and they had some dependency error too or it said something like depended on kaffeine but it's not configured. But when I looked in Synaptic it should the new versions installed. So I looked in my K-menu and there was Kaffeine. So I start it and try it and bam I get the crashing just the same as before. So all in all that package didn't help. But thanks for the suggestion and perhaps it would help if I could get it installed/configured correctly? Got any clues?

---

### Post by DeeZiD on 2005-10-24
Here is commandline which should work fine.
just go to the directory where you've extracted the three packages. (cd /.../.../... ...)

```
sudo dpkg -i kaffeine_0.7.1-0deezi1_i386.deb kaffeine-gstreamer_0.7.1-0deezi1_i386.deb kaffeine-xine_0.7.1-0deezi1_i386.deb
```

:) 

Dennis

---

### Post by Jonathan2007 on 2005-10-24
Well I used that command supposedly got it installed and configured correctly. But Kaffeine is still crashing...

---

### Post by DeeZiD on 2005-10-25
If Kaffeine is crashing again, you have to remove the kaffeinerc in .kde/share/config and maybe the config in /.xine

And of course you should use xine. Gstreamer doesn't work properly ;)


Dennis

---

### Post by Jonathan2007 on 2005-10-25
Still crashing

I removed the kaffeinerc file and I tried it and it crashed. Then I tried removing the /.xine file and I couldn't find a config file. I only found a cache file and a win32 something file. I removed both of those and tried it again and it still crashed.

Any other ideas? Thanks for all your help.

---

### Post by Neutrino on 2005-10-26
I have the same problem. You can use VLC it is another video player that plays all kind for video types.
It is working fine.

---

### Post by palmdev on 2005-10-30
I took the recent Debian package, built it for Breezy and - voila - it works! I did not try to apply any ubuntu patches, but anyway they seem to be of minor importance. If you are lazy enough :) you can download the archive with assembled packages from
[http://gladilovich.front.ru/kaffeine-0.7.1-ubuntu-debs.tar.bz2](http://gladilovich.front.ru/kaffeine-0.7.1-ubuntu-debs.tar.bz2)

---

### Post by Jonathan2007 on 2005-11-04
I would try that package but the link seems dead...

---

### Post by bryan986 on 2005-11-04
I gave up trying to fix kaffeine, there are better alternatives out there...

---

### Post by Jonathan2007 on 2005-11-05
What alternatives that are better? I don't want to use Gstreamer. I want to use Xine. Totem looked pretty ugly when I last saw it. VLC looks bad in KDE. Mplayer is ok but it is not a pure video player which can be ok but eh... Please do list some alternatives though as I am willing to try other stuff if I can't get Kaffeine working.

---

### Post by bryan986 on 2005-11-05
Totem and VLC are probably the best, they work great

Who cares what they look like, is the point not to get one that works? Normally you are paying attention to the video and not the player itself

---

