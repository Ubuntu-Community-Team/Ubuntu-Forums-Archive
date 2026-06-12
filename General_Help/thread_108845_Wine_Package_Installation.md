---
title: "Wine Package Installation"
date: 2005-12-27
forum: General Help
---

### Post by mendy on 2005-12-27
Hi, I'm trying to install the wine package, and I'm using Synaptic.
Nothing is downloading, as the  "Downloading package file" window is just sitting there. f
And the download rate is unknown.
Could it be that the server is down now?

I actually tried earlier today and it started downloading but it said it estimated an hour and a half for the download(!!) so I canceled in the middle.
Could that have something to do with it?

By the way heres the error I get after waiting 5 min.
W: Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.3-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.3-winehq-1_i386.deb)
  Connection failed

Any help would be greatly appreciated

---

### Post by duan on 2005-12-27
Get the lastest straight from winehq by following their tailored install for ubuntu. It worked wonders for me last night, i got version 0.9.3.

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by jsmidt on 2005-12-27
duan, 
    you might have downloaded one noight too early.  I heard 9.4 just came out.

---

### Post by duan on 2005-12-28
I tried update/upgrading but it seems 0.9.3 is the latest repository.

so I got the wine source from cvs
[http://www.winehq.com/site/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE](http://www.winehq.com/site/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE)

I missed the flex and bison installs needed to compile which I just marked and installed with synaptic.

compile and install went fine but it would not run:
libwine.so.1: cannot open shared object file

but I browsed around and did this:

sudo -s
echo "/usr/local/lib" >> /etc/ld.so.conf
ldconfig

now I have:
dj@sprinkaan:~$ wine --version
Wine 0.9.4
dj@sprinkaan:~$

but trying to play UFO Aftermath it still complains that I have no disc inserted when I run the exe !!

---

### Post by shin on 2005-12-28
[QUOTE=duan]
but trying to play UFO Aftermath it still complains that I have no disc inserted when I run the exe !![/QUOTE]

Which is not wine installation problem.
Dunno about current situation but to run game with wine you usually had to have no-cd version (full install and if it doesn't work - no-cd crack).

---

### Post by duan on 2005-12-28
You're right. The install is OK.

the game is another issue.

Furthermore I think the wine-maintained package v0.9.3 is simpler to install and from what I got it seemed more consistent than the v0.9.4 I compiled.

---

