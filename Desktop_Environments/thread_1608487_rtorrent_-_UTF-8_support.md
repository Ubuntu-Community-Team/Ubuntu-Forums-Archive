---
title: "rtorrent - UTF-8 support"
date: 2010-10-29
forum: Desktop Environments
---

### Post by dJe781 on 2010-10-29
Hi fellows !

I'm facing an issue that I've been struggling with for over three days, and by now I'm just not sure that anything I'm doing can actually fix something instead of making things worse. That's why I need help, and I figured that it's the best place to get some :]

Here's the situation :
I'm running a Ubuntu 10.04 Desktop with rtorrent/rutorrent. It fails at properly handling accentuated characters, even though I'm pretty sure that every single brick has UTF-8 enabled. As the problem occurs directly in rtorrent, I figured that searching for problems in rutorrent was irrelevant.
How do I know that it's broken ? Because accentuated characters are replaced by something that looks like a white space (but may not be). If I call for a command input, with Ctrl+X, and try to type "é", nothing is displayed.

What I already know :
- it's likely that Ubuntu itself is working fine. Accentuated characters are properly handled by ssh. A "echo é" command confirmed it.
- UTF-8 seems to be properly configured, as far as I can tell. Here's the output of a "locale" :
> LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
- rtorrent should be ready to handle UTF-8. I added "encoding_list = UTF-8" to the .rtorrent.rc configuration file. As a side note, a friend of mine who's running a Gentoo install tells me that he didn't do anything to make rtorrent handle UTF-8 properly. So I gave a try without encoding_list, which was a dead end.
- I tried to test rtorrent from the Ubuntu package repository without success, however it may not be a proper install because of some overlapping with the previously manually compiled binaries.

What I think :
- I think that somewhere in the process I may have screwed a few things up. I've downloaded and compiled xmlrpc-c, libtorrent and rtorrent myself a couple of times because of [this](http://libtorrent.rakshasa.no/ticket/1316) ticket.
- I'm not sure if the problem comes from rtorrent or Ubuntu. One's may state that Ubuntu being able to handle UTF-8 successfully it's likely to point to rtorrent's responsibility, but I'm just not sure anymore.

I'd be glad if anyone could help me over here, since I'm kind of drowning into doubt and despair ;)

Thanks !

---

### Post by dJe781 on 2013-01-03
Since someone has just approached me about a solution for this one, here's the simpliest one : I just had to force FileZilla into using UTF-8 instead of detecting the charset when I uploaded the .torrent file to this ubuntu server.

Hope it helps !

---

