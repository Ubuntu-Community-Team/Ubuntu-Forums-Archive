---
title: "quake2 demo problem"
date: 2006-10-04
forum: Gaming &amp; Leisure
---

### Post by blackdalek on 2006-10-04
Trying to install quake2 demo.
I was following instructions here [http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html](http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html)
and I downloaded the windows demo from ID software website.
After following all the instructions in how-to (except for "mv Install/Data/baseq2 ." which just makes an error), below is all I get from terminal when I try to run it...

Added packfile ./baseq2/pak2.pak (2 files)
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
recursive shutdown
Error: Couldn't load pics/colormap.pcx



...obviously something is missing, but what? How do I fix this?

---

### Post by blackdalek on 2006-10-05
I still haven't been able to work this out.
Surely someone in here knows how to get this working? Please tell me where I've gone wrong. Thank you.

---

### Post by deadlydeathcone on 2006-10-05
You are doing this in about the most convoluted way possible, as there are packages in the repository that make the process incredibly easy.

Enter

```
sudo apt-get install quake2 quake2-data
```

in a terminal, and it will run a configuration script that will install the demo using wget or the entire game if you have it on a cd (or possibly an image).

You can change what it chooses to install later on by running
```

sudo dpkg-reconfigure quake2-data

```

Hope that works somewhat. :o

---

