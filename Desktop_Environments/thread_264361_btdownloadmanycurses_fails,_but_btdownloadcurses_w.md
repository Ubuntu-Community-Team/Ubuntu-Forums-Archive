---
title: "btdownloadmanycurses fails, but btdownloadcurses works"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Cronjob on 2006-09-24
I'm familiar with the bittorrent-downloader command line interface, but am having the following problem with it under 6.06 (kubuntu):

_These work:_
> btdownloadheadless <filename.torrent>
btdownloadcurses <filename.torrent>

_This does not:_
> btlaunchmanycurses /path/to/torrents

Using btlaunchmanycurses results in the curses interface launching, displaying a row for each of the torrent files that are in the given path, but then underneath each, saying **died, retrying**.

All I can find googling is a snip or two of submitted patches that are unrelated, but contain "died, retrying". Is there something curses related that I need to upgrade or install that I'm somehow not aware of? According to the *man*, --spew won't do anything in curses mode, so . . .

Much thanks in advance for any guidance or suggestions.

---

