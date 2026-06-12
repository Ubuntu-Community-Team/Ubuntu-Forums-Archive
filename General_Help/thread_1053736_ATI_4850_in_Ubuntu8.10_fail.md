---
title: "ATI 4850 in Ubuntu8.10 fail"
date: 2009-01-28
forum: General Help
---

### Post by otara on 2009-01-28
my graphic accelerated meet with broken. in terminal i found this message.who's can help me?

--------------------
The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: fglrx-kernel-source but it is not going to be installed
E: Broken packages
-------------------
The following packages have unmet dependencies:
  fglrx-kernel-source: Depends: dkms but it is not installable
E: Broken packages
-------------------
Package dkms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dkms has no installation candidate
-------------------

when i test in terminal, i get
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

---

### Post by rbmorse on 2009-01-29
From the main menu in the top panel:

system > administration > hardware drivers

click on the "activate" button and let it run.  When it's finished, open a terminal and run the command:

sudo aticonfig --initial -f

when that's finished, close the terminal window and restart the video server by pressing <ctrl><alt><backspace>.

---

