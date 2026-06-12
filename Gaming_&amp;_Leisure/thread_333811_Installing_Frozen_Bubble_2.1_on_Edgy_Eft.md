---
title: "Installing Frozen Bubble 2.1 on Edgy Eft"
date: 2007-01-08
forum: Gaming &amp; Leisure
---

### Post by pierre.s.rosen on 2007-01-08
I am having difficulty installing Frozen Bubble 2.1 on Edgy Eft 6.10

I followed the directions on [http://www.frozen-bubble.org/downloads/](http://www.frozen-bubble.org/downloads/) which state:
Ubuntu: users of edgy can add deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) edgy-darkmagez games to their /etc/apt/sources.list ... then type apt-get update && apt-get install frozen-bubble to install 2.1.0

I got this error:

W: GPG error: [http://mirror.randumb.org](http://mirror.randumb.org) edgy-darkmagez Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB5D6B0AA3012FB3
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Then I tried  wget [http://mirror.randumb.org/darkmagez/repo/DB5D6B0AA3012FB3.gpg](http://mirror.randumb.org/darkmagez/repo/DB5D6B0AA3012FB3.gpg) - O | sudo apt-key add - and got this error:

Password:--00:03:37--  [http://mirror.randumb.org/darkmagez/repo/DB5D6B0AA3012FB3.gpg](http://mirror.randumb.org/darkmagez/repo/DB5D6B0AA3012FB3.gpg)
           => `DB5D6B0AA3012FB3.gpg'
Resolving mirror.randumb.org... 66.152.171.198
Connecting to mirror.randumb.org|66.152.171.198|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:03:37 ERROR 404: Not Found.

--00:03:37--  [http://-/](http://-/)
           => `index.html'
Resolving -... failed: Name or service not known.
--00:03:38--  [http://o/](http://o/)
           => `index.html'
Resolving o... failed: Name or service not known.

FINISHED --00:03:38--
Downloaded: 0 bytes in 0 files

Any ideas on what I am doing wrong?  Is there a better way to install frozen bubble 2.1?](*,)

---

### Post by Perfect Storm on 2007-01-08
There's a howto compiling Frozen Bubble 2 on the howto section of Ubuntu Gamers Arena. 

The bad news is the servers (which KB hosted) ran into a storm weather which took them out, so you might wait a bit yet.

---

### Post by pierre.s.rosen on 2007-01-08
I was able to find the directions using google's chache of the page here: [http://209.85.165.104/search?q=cache:FdVlQEwq9_gJ:gaming.gwos.org/index.php%3Foption%3Dcom_content%26task%3Dview%26id%3D187%26Itemid%3D63+site:gwos.org+frozen+bubble&hl=en&gl=us&ct=clnk&cd=2&client=firefox-a](http://209.85.165.104/search?q=cache:FdVlQEwq9_gJ:gaming.gwos.org/index.php%3Foption%3Dcom_content%26task%3Dview%26id%3D187%26Itemid%3D63+site:gwos.org+frozen+bubble&hl=en&gl=us&ct=clnk&cd=2&client=firefox-a)

Basic rehash:
1) Make sure you have 3D drivers installed and enabled.
2) sudo aptitude update && sudo aptitude upgrade
3) sudo aptitude install build-essential checkinstall
4) sudo aptitude install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-perl libpango1.0-dev
5) Download SDL_Pango-0.1.2.tar.gz ([http://sourceforge.net/project/showfiles.php?group_id=110621](http://sourceforge.net/project/showfiles.php?group_id=110621)) and SDL_Pango-0.1.2-API-adds.patch ([http://zarb.org/%7Egc/t/SDL_Pango-0.1.2-API-adds.patch](http://zarb.org/%7Egc/t/SDL_Pango-0.1.2-API-adds.patch)) to your Desktop.
6) cd && cd Desktop
7) tar zxfv SDL_Pango-0.1.2.tar.gz
8 ) cd SDL_Pango-0.1.2
9) patch -p0 <../SDL_Pango-0.1.2-API-adds.patch
10) ./configure --prefix=/usr
11) make
12) sudo checkinstall
13) Download Frozen Bubble source code ([http://www.frozen-bubble.org/data/frozen-bubble-2.1.0.tar.bz2](http://www.frozen-bubble.org/data/frozen-bubble-2.1.0.tar.bz2)) to your Desktop.
14) cd && cd Desktop
15) tar jxfv frozen-bubble-2.1.0.tar.bz2
16) cd frozen-bubble-2.1.0
17) make
18 ) sudo make install
19) sudo checkinstall
20) sudo nano /usr/share/applications/FrozenBubble2.desktop
21) Add the following to the file:
Add the following;

[Desktop Entry]
Name=Frozen Bubble 2
Comment=GPL Arcade Game
Exec=frozen-bubble
Icon=/usr/local/share/frozen-bubble/gfx/menu/small_ping.png
Terminal=false
Type=Application
Categories=Application;Game;
22) Save (ctrl) + (o) and exit (ctrl) + (x)
23) Frozen Bubble 2 should now be usable using the Applications tab ---> Games ---> Frozen Bubble 2 or by typing frozen-bubble in the terminal.  :D 
24) You can uninstall the game by using synaptic or your apt program of choice, if you so choose.

---

