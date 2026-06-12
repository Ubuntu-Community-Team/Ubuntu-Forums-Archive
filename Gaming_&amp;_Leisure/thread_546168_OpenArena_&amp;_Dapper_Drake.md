---
title: "OpenArena &amp; Dapper Drake"
date: 2007-09-08
forum: Gaming &amp; Leisure
---

### Post by Ignoramus on 2007-09-08
How do I install OpenArena 0.7.0 on Ubuntu 6.06?

---

### Post by DoktorSeven on 2007-09-08
[http://openarena.ws/](http://openarena.ws/)

Download the WIndows/Linux zip archive, extract it in your home directory.  Might need to change permissions on the executable.

---

### Post by Ignoramus on 2007-09-08
Oh, okay. Thanks. :)

---

### Post by DoktorSeven on 2007-09-08
The executables are the ioquake3* files, by the way.  -smp are for multiproc systems, x86_64 is 64bit, and i386 is 32bit, so run whatever's appropriate.  (ioq3ded* is for a dedicated server -- you likely don't want these.)

If it won't run, run it via a terminal and see what is output.  If it complains that a library is missing, search for its name in Synaptic or with apt-cache search and install the most likely candidate.

Also grab the 0.71 patch and extract it in the same place you extracted 0.70, it should place the pk3 file in the correct place (openarena-0.7.0/baseoa/).

You can make a desktop shortcut by creating a file like this:

```

#!/bin/bash

cd ~/openarena-0.7.0/
# if you extracted it somewhere other than your home directory, change the line above
./ioquake3.i386 
# or if you use 64bit and/or multiprocessor, change the binary name above

```

Make it executable (either through its properties in your file manager or with **chmod +x *whatever you called the file***.  You can now link to that script in your menu, as a desktop icon, or in quick launch.  You might have to find an appropriate icon, though.

---

