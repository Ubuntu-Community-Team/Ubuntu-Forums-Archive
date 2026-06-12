---
title: "Emulations?"
date: 2006-01-12
forum: Gaming &amp; Leisure
---

### Post by bensode on 2006-01-12
Any suggestions on emulators with Ubuntu for old Commodore ROMS?  Maybe even MAME?  Sometimes the best games are the oldies but goodies ;)

---

### Post by BoyOfDestiny on 2006-01-13
[QUOTE=bensode]Any suggestions on emulators with Ubuntu for old Commodore ROMS?  Maybe even MAME?  Sometimes the best games are the oldies but goodies ;)[/QUOTE]

Advancemame and advancemenu hands down.

Works both in x86 and amd64 (that I've tested anyway)


[http://advancemame.sourceforge.net/](http://advancemame.sourceforge.net/)

it's not in the repos, my debs made with checkinstall are here: [www.safaribans.com/gpl](www.safaribans.com/gpl)

They are a little out of date

to install use 

sudo dpkg -i nameofdeb.deb

For advancemame and menu, there is one document file both have, and this confused checkinstall I guess... so if you run into a problem

sudo dpkg -force-all nameofdeb.deb

will do the trick. :)


As for c64, I've been trying to get vice to work, the one in the repos AFAIK does not contain the commodore kernal (this is not a typo...). 

[http://www.viceteam.org/](http://www.viceteam.org/)

I've been trying to build it, but I haven't tested any recent versions... 

Feel free to mention other c64 emus for linux (I'm particularly interested in those that can run in x86 and amd64)

---

### Post by antivert on 2006-07-06
All you need are the commodore firmware roms. They're still available at: 

[http://cvsup.de.openbsd.org/historic/comp/os/c64/VICE/vice-1.5-roms.tar.gz](http://cvsup.de.openbsd.org/historic/comp/os/c64/VICE/vice-1.5-roms.tar.gz)

That's the only place I'm seeing that still has the archive, maybe someone should mirror that! At any rate, just untar it, then cd to the data/ dir it makes, and sudo cp -R * /usr/lib/vice/ and you should be set. That just puts the files from the archive into the respective directories (C64, C128, etc) in /usr/lib/vice. 

Enjoy!

---

### Post by bsantos on 2006-07-13
They're in the source package. :)

[http://www.viceteam.org/online/1.19/vice-1.19.tar.gz](http://www.viceteam.org/online/1.19/vice-1.19.tar.gz)

And use the data directory as your $HOME/.vice ;)

The packager of vice could add this, or is there any issue with these roms?

---

### Post by Ptero-4 on 2006-07-13
It probably will have legal issues like the ones with most gaming console roms.

---

### Post by Vicfred on 2006-07-14
where can i find gba roms and emulators?

**Please desist from asking for Illegal material -- KB.**

---

