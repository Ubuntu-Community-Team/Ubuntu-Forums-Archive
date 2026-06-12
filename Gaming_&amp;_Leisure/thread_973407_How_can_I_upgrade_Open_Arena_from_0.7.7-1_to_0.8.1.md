---
title: "How can I upgrade Open Arena from 0.7.7-1 to 0.8.1?"
date: 2008-11-06
forum: Gaming &amp; Leisure
---

### Post by diablo75 on 2008-11-06
A friend of mine (who's running Windows) wants to play some games over the net with me.  If it were up to me, I'd go with Quake III, but I can't for the life of me find my CD case with the serial number on it so it's out of the question.  So I'd like to see how Open Arena would be.

I currently have Open Arena installed in Ubuntu, via Synpatic.  According to synaptic, the version I have installed is 0.7.7-1.  But according to the open arena website, the latest version available is 0.8.1.

[http://openarena.ws/files.html](http://openarena.ws/files.html)

Is there a way for me to upgrade to the next version, or perhaps install the latest version via synaptic?

---

### Post by anjilslaire on 2008-11-06
you can get 0.8.0 from [**getdeb**]("http://www.getdeb.net/app/OpenArena"). Or, the Open Arena site you linked has 6 places to download the latest & greatest from:

[http://www.moddb.com/games/openarena/downloads/openarena-081-zip-archive](http://www.moddb.com/games/openarena/downloads/openarena-081-zip-archive)
[http://download.tuxfamily.org/openarena/rel/081/oa081.zip](http://download.tuxfamily.org/openarena/rel/081/oa081.zip)
[http://www.atomicgamer.com/file.php?id=73011](http://www.atomicgamer.com/file.php?id=73011)
[http://www.gamershell.com/download_35268.shtml](http://www.gamershell.com/download_35268.shtml)
[http://files.filefront.com/oa081zip/;12213474;/fileinfo.html](http://files.filefront.com/oa081zip/;12213474;/fileinfo.html)
[http://www.fileshack.com/file_partner.x?f=moddb/2008%2F10%2F31%2Foa081.zip&t=OpenArena+0.8.1+ZIP+archive+for+OpenArena&g=OpenArena&u=http%3A%2F%2Fwww.moddb.com%2Fgames%2Fopenarena%2Fdownloads%2Fopenarena-081-zip-archive&s=318927645](http://www.fileshack.com/file_partner.x?f=moddb/2008%2F10%2F31%2Foa081.zip&t=OpenArena+0.8.1+ZIP+archive+for+OpenArena&g=OpenArena&u=http%3A%2F%2Fwww.moddb.com%2Fgames%2Fopenarena%2Fdownloads%2Fopenarena-081-zip-archive&s=318927645)

---

### Post by DoktorSeven on 2008-11-07
Games that aren't in the repositories, just download and update like you would a Windows game that just comes packaged as a zip file (non-installable).

Download the game via their site, extract to your home directory.  Should give you an "openarena-0.8.1" directory.  Create a text file like this:

```

#!/bin/bash
cd ~/openarena-0.8.1
./openarena.i386

``` 
(Substitute ./openarena.x86_64 if you're on 64-bit)

Save it somewhere, make it executable (check the executable bit in the file properties or **chmod +x openarena-launcher** (or whatever you called it) from the commandline.

Make a shortcut that points to it, grab an icon from somewhere to decorate it (or not).

Sure, it's a little legwork, but you get used to it.  Not everything can be automatically done for you. :)

---

