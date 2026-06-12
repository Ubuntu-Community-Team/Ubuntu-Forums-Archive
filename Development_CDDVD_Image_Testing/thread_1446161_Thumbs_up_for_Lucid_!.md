---
title: "Thumbs up for Lucid !"
date: 2010-04-03
forum: Development CD/DVD Image Testing
---

### Post by WitchCraft on 2010-04-03
It works very well, and is quite fast.

Bug: The Kazehakase browser can be installed and started, but you can't browse to any website with it (does not react)...

Bug: Needed to start twice until the installation process started correctly.

Bug: Needed to start twice after the installation process finished until it worked correctly.

---

### Post by Naitsirhc Hsem on 2010-04-03
I have been using it on both of my computers and am loving it

---

### Post by WitchCraft on 2010-04-04
> **Naitsirhc Hsem said:**
> I have been using it on both of my computers and am loving it

It's extremely fast, compared to the last version.
And all the restricted-extras work without problems, and I no longer have to allow root login, it works out of the box.
I love it !

Note for NVIDIA and ATI users:
> 
"envyng-gtk/qt" in Lucid Lynx is superseded by jockey. 


Another bug:
Trying to compile soundkonverter via apt-get buid-dep and apt-get source doesn't work, because the two .h files below miss #include <stdio.h> .
Add #include <stdio.h> to both these files:
/usr/src/soundkonverter-0.3.11/src/metadata/audible/audibleproperties.h
/usr/src/soundkonverter-0.3.11/src/metadata/wav/wavproperties.h


Though VLC still does not work out of the box when run as root. 
You need to recompile it and remove uid == 0 from VLC.c. 
I just compiled vlc with this code commented out from source in bin/vlc.c file:

Remove the bellow code snippet
```

/*    
// Remove from bin/vlc.c
if (geteuid () == 0)
    {
        fprintf (stderr, "VLC is not supposed to be run as root. Sorry.\n"
        "If you need to use real-time priorities and/or privileged TCP ports\n"
        "you can use %s-wrapper (make sure it is Set-UID root first and\n"
        "cannot be run by non-trusted users first).\n", ppsz_argv[0]);
        return 1;
    }
*/

```

and it works !

And another bug:
apt-get install dpkg-dev

should be installed by default, because else it stops when doing apt-get source xy

---

### Post by trig on 2010-04-11
What is jockey?

---

### Post by WitchCraft on 2010-04-13
> **trig said:**
> What is jockey?

A program that downloads, installs and configures the correct NVIDIA/ATI OpenGL driver for you.

---

