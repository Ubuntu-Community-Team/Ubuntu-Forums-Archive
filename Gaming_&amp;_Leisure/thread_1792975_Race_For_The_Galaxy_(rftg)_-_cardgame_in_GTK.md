---
title: "Race For The Galaxy (rftg) - cardgame in GTK"
date: 2011-06-28
forum: Gaming &amp; Leisure
---

### Post by Mozai on 2011-06-28
Among boardgamers there's a well-known card game called [Race For The Galaxy]("http://www.boardgamegeek.com/game/28143").  I found that a software version was made, with computer opponents and network play.  It compiled easily on my Ubuntu 11.04 workstations, looks slick, so I want to tell people about it.

The website is for the software is [http://www.keldon.net/rftg/](http://www.keldon.net/rftg/).  Building it was a simple './configure && make && sudo make install' and it installs to /usr/local/*

I couldn't say what packages needed to be installed to compile it properly ('./configure' should give hints) but I can say what packages provided the libraries linked in:

[SIZE="1"]
libatk1.0-0
libc6
libcairo2
libexpat1
libfontconfig1
libfreetype6
libgdk-pixbuf2.0-0
libglib2.0-0
libgtk2.0-0
libpango1.0-0
libpcre3
libpixman-1-0
libpng12-0
libselinux1
libx11-6
libxau6
libxcb1
libxcb-render0
libxcb-shm0
libxcomposite1
libxcursor1
libxdamage1
libxdmcp6
libxext6
libxfixes3
libxi6
libxinerama1
libxrandr2
libxrender1
zlib1g[/SIZE]

---

### Post by Kaparen on 2011-07-03
From a fresh install, libgtk2.0-dev was all I needed to get it running on Natty.

---

### Post by Tweak42 on 2012-08-27
> **Kaparen said:**
> From a fresh install, libgtk2.0-dev was all I needed to get it running on Natty.

Thanks, I also needed to install libgtk2.0-dev to compile in 12.04.  I also did get the windows .exe running under Wine, but nice to know it can be built natively.

---

