---
title: "torrent downloads in ubuntu server"
date: 2006-08-23
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-23
How can torrents be downloaded from the command line? My computer boots into run level 3, and I only bring up the graphics once in a while. I found several programs, but I am not sure which one is used for downloading. Some of these programs may be for using Linux as a torrent tracker. If you want to find out about these same programs, just type bt and hit tab twice.

```
chris@ubuntu:~/CD IMAGES$ bt
btcompletedir                  btmakemetafile
btcompletedir.bittorrent       btmakemetafile.bittorrent
btdownloadcurses               btreannounce
btdownloadcurses.bittorrent    btreannounce.bittorrent
btdownloadheadless             btrename
btdownloadheadless.bittorrent  btrename.bittorrent
btlaunchmany                   btshowmetainfo
btlaunchmany.bittorrent        btshowmetainfo.bittorrent
btlaunchmanycurses             bttrack
btlaunchmanycurses.bittorrent  bttrack.bittorrent
chris@ubuntu:~/CD IMAGES$ bt
```

[I looked here for some documentation. I couldn't find any.]("http://www.bittorrent.com/index.html")

I read the man pages of many of the bt files.

[Look at the description here.]("http://packages.ubuntu.com/dapper/net/bittorrent")
```

chris@ubuntu:~/CD IMAGES$ apt-cache show bittorrent
Package: bittorrent
Priority: optional
Section: net
Installed-Size: 580
Maintainer: Michael Janssen <jamuraa@debian.org>
Architecture: all
Version: 3.4.2-6ubuntu2
Depends: python (<< 2.5), python (>= 2.4), lsb-base (>= 3)
Recommends: mime-support
Suggests: bittorrent-gui
Filename: pool/main/b/bittorrent/bittorrent_3.4.2-6ubuntu2_all.deb
Size: 94208
MD5sum: ba31ae27f0edad4d1434ab75bd840fb7
Description: Scatter-gather network file transfer
 BitTorrent is a tool for distributing files. It's extremely
 easy to use - downloads are started by clicking on hyperlinks.
 Whenever more than one person is downloading at once
 they send pieces of the file(s) to each other, thus relieving
 the central server's bandwidth burden. Even with many
 simultaneous downloads, the upload burden on the central server
 remains quite small, since each new downloader introduces new
 upload capacity.
 .
 This package contains the tools which are used for console-only
 downloading.  If you want the GUI interface, install the
 bittorrent-gui package.
 .
  Homepage: http://bitconjurer.org/BitTorrent/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop

chris@ubuntu:~/CD IMAGES$
```

---

### Post by daageep on 2006-09-16
I use btlaunchmanycurses (i think it was from the bittornado package). this is the version that downloads ALL .torrents from the specified directory.

so i save all the .torrent files into the current directory then run > btlaunchmanycurses ./ --minport 6881 --maxport 6999

this will download all the torrents in the directory.

---

