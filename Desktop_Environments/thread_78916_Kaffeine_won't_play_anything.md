---
title: "Kaffeine won't play anything"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Pumpino on 2005-10-19
Kaffeine won't play mp3s or mpegs on either on my machines running Breezy.  I haven't been able to install w32codecs via Synaptics, and it can't seem to retrieve them from the mirror.  I had w32codecs deb from Hoary, so I installed that using dpkg.  How can I get it to play files and stop complaining about missing codecs?

EDIT:  I apologise.  I see there's an existing thread located
[http://ubuntuforums.org/showthread.php?t=78535](http://ubuntuforums.org/showthread.php?t=78535)

---

### Post by derrick1985 on 2005-10-19
[QUOTE=Pumpino]Kaffeine won't play mp3s or mpegs on either on my machines running Breezy.  I haven't been able to install w32codecs via Synaptics, and it can't seem to retrieve them from the mirror.  I had w32codecs deb from Hoary, so I installed that using dpkg.  How can I get it to play files and stop complaining about missing codecs?[/QUOTE]

First of all, do you have the universe/multiverse repos enabled?

Also, if you want w32codecs, you can use the debian repository, but ONLY GET w32codecs!!! if you get anything else, it can potentially screw up your system.

 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

Also, after you have all that done, read this section of the Ubuntuguide and you should be on your way.

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

that's what got it all working for me.

---

