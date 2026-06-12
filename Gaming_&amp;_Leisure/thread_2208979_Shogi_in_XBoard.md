---
title: "Shogi in XBoard"
date: 2014-03-03
forum: Gaming &amp; Leisure
---

### Post by zelphir2 on 2014-03-03
Hi,

So I was trying to find a GUI for playing Shogi on Ubuntu. I only found xshogi and xboard.
I saw that the xboard GUI looked better than the xshogi version, but I could not get xboard to simply start a shogi game.

This is what the "New Variant" dialog looks like:
[IMG]http://im.bilderkiste.org/5139385418073/XboardScreenshot.png[/IMG]

I have absolutely no idea why Shogi is disabled, like many other options, not even Fisher Random Chess is enabled o0. I tried changing the values at the bottom of the dialog but nothing changed. I searched the web and couldn't find any forum post or anything describing the same issue. What is the cause for Shogi being disabled here? What do I need to do to enable it? I've read about other users playing Shogi using xboard so it shouldn't be too hard to get it running somehow.

---

### Post by Darklord42 on 2014-10-25
I know it's been a while since this was posted, but in case anyone else sees this.

The reason most of the variants are greyed out is because you can only play the variants that the loaded engine supports.  Load an engine that supports shogi. Or launch xboard without an engine to access them all (-ncp).  You can find a binary of Harm Geert Muller's Shokidoki on his website [http://home.hccnet.nl/h.g.muller/shokidoki.html](http://home.hccnet.nl/h.g.muller/shokidoki.html), and there are two sources of engine you can compile yourself [http://hgm.nubati.net/cgi-bin/gitweb.cgi](http://hgm.nubati.net/cgi-bin/gitweb.cgi) .  A special branch of gnushogi that speaks xboard protocol and a version of Bonanza 6.0 that speaks xboard. (you must download the supporting files for Bonanza 6.0 on their website)   Also on that site you can download and compile the UCI2WB adapter which supports USI protocol with the -s flag.  GPS shogi is the only open source USI engine I'm aware of.

---

### Post by Darklord42 on 2014-10-26
Thankfully, new versions of xboard explain this in the blurb on the lower left of the variants window.

---

