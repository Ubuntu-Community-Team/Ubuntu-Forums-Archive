---
title: "Open Raider"
date: 2009-01-28
forum: Gaming &amp; Leisure
---

### Post by david1993 on 2009-01-28
I just finished successfully installing Open Raider (for those who dont know it is an open source version of tomb raider). But I need Help running it, I can not find it in my applications menu. I pressed alt+f2 and tried typing in openraider, Open Raider, and i also tried OpenRaider, but i cant get it to run. Just to make sure it was installed opened Synaptic and sure enough it is installed. How do I run it!?

---

### Post by graabein on 2009-01-28
Have you tried looking up info on the package? 

[http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html")

**apt-cache show stella**
```

     Package: stella
     Priority: extra
     Section: non-free/otherosfs
     Installed-Size: 830
     Maintainer: Tom Lear <tom@trap.mtview.ca.us>
     Architecture: i386
     Version: 1.1-2
     Depends: libc6 (>= 2.1), libstdc++2.10, xlib6g (>= 3.3.5-1)
     Filename: dists/potato/non-free/binary-i386/otherosfs/stella_1.1-2.deb
     Size: 483430
     MD5sum: 11b3e86a41a60fa1c4b334dd96c1d4b5
     Description: Atari 2600 Emulator for X windows
      Stella is a portable emulator of the old Atari 2600 video-game console
      written in C++.  You can play most Atari 2600 games with it.  The latest
      news, code and binaries for Stella can be found at:
      http://www4.ncsu.edu/~bwmott/2600
```

Use the find command to search... 

[http://linux.about.com/od/commands/a/blcmdl1_findx.htm]("http://linux.about.com/od/commands/a/blcmdl1_findx.htm")

---

### Post by KIAaze on 2009-01-28
It should be here:
```
/usr/games/OpenRaider
```
:)

_**How to find out where binaries get installed:**_

Here are several ways you can see what got installed by a package:
1)List the contents of the .deb package:
```
dpkg -L PACKAGE
dpkg -c PACKAGE

```

2)Browse the contents of the .deb package:
a)with midnight commander:
```
sudo apt-get install mc\
mc
```
(mouse is usable inside it! :) )
It requires dpkg to be able to browse package contents, but dpkg should already be installed by default in Ubuntu.

b)with an archive manager like file-roller (installed by default) or ark:
```
file-roller PACKAGE
ark PACKAGE
```

c)Konqueror (nautilus perhaps too, not sure) also allows viewing the contents of a .deb package.
Just right-click and select "preview in archiver". (uses embedded Ark I believe)

3)In Synaptics, look at the package properties. There should be an "installed files" tab. (I'm on OpenSUSE right now, so i don't know exactly where.)

4)In the case of packages from the official repositories, you can click on "list files" when you view a package on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
ex: [http://packages.ubuntu.com/intrepid/i386/mc/filelist](http://packages.ubuntu.com/intrepid/i386/mc/filelist)

In all cases, look for the files that are in "bin" or "games" directories, since this is where binaries usually get installed (/bin, /usr/bin, /user/local/bin, etc).

---

