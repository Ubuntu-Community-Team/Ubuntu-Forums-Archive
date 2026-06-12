---
title: "Equivalent of Alcohol 120%?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by veraction on 2005-10-23
Anyone know of any free CD/DVD emulation software for linux?

guess I can do iso via mount, but what about bin/cue

[edit] nvm, found [CDemu]("http://cdemu.sourceforge.net/") dunno how to install it with the kernel source

---

### Post by 3david on 2005-10-23
I use a program called isodump to convert bin/cue files to iso:

[http://www.icewalkers.com/Linux/Software/52630/isodump.html](http://www.icewalkers.com/Linux/Software/52630/isodump.html)

In addition to cdemu, there's also a program called cdfs (it's sources appear in the ubuntu repositories: apt-cache search cdfs), i'm not sure if it would help, but here's the link anyway: [http://www.elis.rug.ac.be/~ronsse/cdfs/](http://www.elis.rug.ac.be/~ronsse/cdfs/)

btw, 
-to mount iso files with "mount":
  mount -o loop $isofile $mount_dir

-to play bin/cue files with "mplayer":
  mplayer cue://$cue_file

---

