---
title: "gamespot video streams"
date: 2005-05-18
forum: Desktop Environments
---

### Post by vegetto on 2005-05-18
I want watch all the cool e3 streams from gamespot but i can't in ubuntu. i installed mozplugger and also installed mozpluggerrc for totem-xine but i still get that dumb puzzle icon with a missing plugin message. and installing mplayer is not an option 
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but it is not going to be installed
E: Broken packages 
help would be appreciated.

---

### Post by lorap on 2005-05-18
hi friend!
i'm not currently at my pc so wait for 11/2 hour and once i get home i'll write the package name you've install. but to install it you need to add it to the existing packages.
so to have it on the list do this till i get home:

open Synaptic Package Manager, then go to the Settings-->Repositories.
mark in that window all checkboxes possible regardless any warnings and press Ok.
after what press Reload button.

this'll install add you an extra packages.
you need istall only one package to get everything work.
pavel

---

### Post by bored2k on 2005-05-18
sudo apt-get install kaffeine-mozilla does the trick. I have tested it on windows m. videos [i too watch gspot videos].

and mplayer also works.

---

### Post by bored2k on 2005-05-18
[QUOTE=lorap]hi friend!
i'm not currently at my pc so wait for 11/2 hour and once i get home i'll write the package name you've install. but to install it you need to add it to the existing packages.
so to have it on the list do this till i get home:

open Synaptic Package Manager, then go to the Settings-->Repositories.
mark in that window all checkboxes possible regardless any warnings and press Ok.
after what press Reload button.

this'll install add you an extra packages.
you need istall only one package to get everything work.
pavel[/QUOTE]
 That made no sense at all.

---

### Post by lorap on 2005-05-18
hi friend!
the package's name's:
gstreamer0.8-ffmpeg

---

