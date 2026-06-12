---
title: "Unable to install SCORCHED 3D - openal error"
date: 2005-12-12
forum: Gaming &amp; Leisure
---

### Post by infoseeker on 2005-12-12
I have installed everything referring to openal in Synaptic, but I still get the following error:
> checking for OpenAL... checking for openal-config... no
*** The openal-config script installed by OpenAL could not be found
*** Make sure openal-config is in your path, or set the OPENAL_CONFIG
*** environment variable to the full path to openal-config.
checking for OpenAL compilation... no
configure: error: *** Can't find the openal library. Try: [http://www.openal.org/](http://www.openal.org/)

I cannot find any drivers for Linux on [http://www.openal.org/](http://www.openal.org/)

Any help?

---

### Post by Perfect Storm on 2005-12-12
```

sudo apt-get install libgl1-mesa libglu1-mesa

```

---

### Post by infoseeker on 2005-12-12
> Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
libglu1-mesa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Thanks anyway :(

---

### Post by Harleen on 2005-12-12
You don't want to build openal for yourself, do you? Because you probably have to...

That missing file was fixed in Debian for the package openal/0.2005080600-2 while Ubuntu uses openal/0.[COLOR="Red"]2004[/COLOR]090900-1

See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=323054](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=323054)

---

### Post by infoseeker on 2005-12-13
I have never applied a patch before.
Can someone please give me details on how to apply this patch.

Thanks

---

### Post by Harleen on 2005-12-13
What patch? You won't get away that easy.

You could either compile openal for yourself. But they don't provide complete source packages for download. You have to get the source with CVS. 

Or you could replace your libopenal packages with the Debian versions if you dare. 

[http://packages.debian.org/testing/libdevel/libopenal-dev](http://packages.debian.org/testing/libdevel/libopenal-dev)
[http://packages.debian.org/testing/libs/libopenal0](http://packages.debian.org/testing/libs/libopenal0)

I officially wouldn't recommend using packages of another distribution. (but unofficially I just did that...)

That solved that error in compiling Scorched3D, but uncovered the next. problem. This time with wxWidget, which I wasn't able to solve.

Using the older version of Scorched3D, that Ubuntu provides will probably cause much less trouble.

---

### Post by infoseeker on 2005-12-13
OK will take your advice.  Thanks anyway  ;)

---

### Post by Darganot on 2008-02-16
> **Harleen said:**
> You have to get the source with CVS. 


HOW!?!?!?

...and don't tell me to search, because this is what I got when I did.

---

### Post by Perfect Storm on 2008-02-16
Dude, check the date of the thread.


Thread closed.

---

