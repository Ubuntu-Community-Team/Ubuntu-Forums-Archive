---
title: "lxDoom, where do the wads go?"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by Drate on 2007-04-01
I see others have had my problem with trying to run lxDoom and nothing happens... then people say, "Oh, well you have to have the WAD files to run them".... great... now what do I DO with these wad files?

Plz help, THANX!

---

### Post by marianom on 2007-05-04
I'm late but let see if you still need this:
Do
```
sudo apt-get install doom-wad-shareware
```
and then run lxdoom again. It should work (because the wad file will be store in the place lxdoom needs it). You need the multiverse repo to make it work.

You can download from here too: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=doom-wad-shareware&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=doom-wad-shareware&searchon=names&subword=1&version=edgy&release=all)

In case you already have the wad file, you can call lxdoom for the command line pointing the place of your wad file:
```
lxdoom -width 640 -height 480 -file /home/mariano/MyStuff/songs.wad
```

---

### Post by Nehvrook on 2007-05-17
What you suggested there worked Marianom, I'm just wondering if anyone knows why I'm getting no sound when playing this game?

---

