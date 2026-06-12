---
title: "Pcsx Ps1"
date: 2006-08-24
forum: Gaming &amp; Leisure
---

### Post by fakie_flip on 2006-08-24
I'm trying to play a few of my old PS1 games in Linux. Will someone with experience using PCSX reply? I'm getting this error. Look in the picture I attached. Nothing happens when I choose PCSX from the gnome menu. For some reason, there is not an icon for PCSX. Maybe it did not install correctly. I already tried reinstalling it.

```
veronica@veronica-desktop:~$ pcsx -runcd
/usr/games/pcsx: line 31: lndir: command not found
veronica@veronica-desktop:~$ apt-cache search lndir
veronica@veronica-desktop:~$
```

---

### Post by bugzor on 2006-08-24
try epsxe ([http://epsxe.com/](http://epsxe.com/))
it works fine with me and its probably best psx emulator anyway

---

### Post by fakie_flip on 2006-08-24
How'd you install it? I'd like to get it from Synaptic or apt-get if possible.

---

### Post by fakie_flip on 2006-08-24
What's the most minimum requirements for a video card with the amount of vram? Sometimes they say you need a heavy duty graphics card, but you can get away with one that's old.

---

### Post by den benne on 2006-08-24
here's a howto for installing/configuring PCSX:

[http://gaming.gwos.org/index.php?option=com_content&task=view&id=13&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=13&Itemid=63)

---

### Post by rschultz on 2006-08-24
Heya; Debian maintainer of the PCSX package and the main developer of the PCSX fork, PCSX-df, here :- )

The old PCSX (non -df) packages require a script to start them that creates a special environment, because PCSX does not support multi-user installs like a Debian package requires. This script links in all of the  PSEmu plugins on the system and creates a place for PCSX to run in without disrupting the system install. However, the script uses the lndir command, which Ubuntu dropped for some reason from their X packages, I guess.

Like many packages, PCSX was pulled from Debian and merged straight into Ubuntu automatically, so this wasn't noticed. A quick packages.ubuntu.com search gave nothing for lndir, so I assume it was totally banished from the Ubuntu X packages.

It looks like Ubuntu edgy has the PCSX-df 1.7 RC versions, which contain proper multi-user system support (and a huge amount of other fixes, as well), but I'm not very familiar with Ubuntu's version compatibility or anything. You might try installing the version of PCSX-df in Edgy.
 [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pcsx&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pcsx&searchon=names&subword=1&version=edgy&release=all)

Alternately, PCSX-df can be built quite easily from source using apt-get to make build dependencies easy:

sudo apt-get build-dep pcsx-bin
wget [http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz](http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz)
tar xzvf pcsx-df-1.7rc3.tar.gz
cd pcsx-df-1.7rc3
./configure --prefix=/usr/local
make
sudo make install

You can use the PSEmu plugins available in apt, although there are newer versions available in Debian unstable and presumably in Edgy.

There are also packages in my archive, but they are built for Debian. You could try to install them as well, if nothing else works. [http://rschultz.ath.cx/debian.php](http://rschultz.ath.cx/debian.php)

Let me know if nothing works ><

---

### Post by caecgirl on 2008-12-09
Why am I always 6 months to 2 years late to finding posts about questions I need answers to.  In case someone is watching this thread for whatever reason.  PCSX opens just fine, and I got plugins setup on it.  I put the game in the cd-rom, and then select run cd or run cd through bios but nothing happens.  I'm not certain of the difference between run cd and run cd through bios, but it had the same result either way.

---

