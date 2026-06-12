---
title: "Make compile stopping at 'all-am'"
date: 2011-07-21
forum: Gaming &amp; Leisure
---

### Post by freshmeat20 on 2011-07-21
Im trying to install the Playstation 1 emulator PCSXR and got to make.This is as far as I got.

```
swerve@swerve-Studio-1440:/root/pcsxr$ make
 cd . && /bin/bash /root/pcsxr/missing --run automake-1.11 --foreign data/Makefile
 cd . && /bin/bash ./config.status data/Makefile 
config.status: creating data/Makefile
make: *** No rule to make target `pcsxr.desktop', needed by `all-am'.  Stop.
```

Anyone think theres a problem with the directory path for the pcsxr.desktop?

---

### Post by freshmeat20 on 2011-07-21
bump...

---

### Post by cipherboy_loc on 2011-07-21
More or less, the issue is that it is trying to compile a .desktop file (aka a GNOME desktop icon), but it doesn't know how.



Cipherboy

---

### Post by freshmeat20 on 2011-07-21
Im using GNOME 2.32... Im guessing its a wrong path in a certain Makefile but theres so many...... Some of which that are re-written everytime ./configure, make, etc is used. I noticed in Makefile.am in /pcsxr/data it declares the .desktop pathway here..

```
glade_DATA = pcsxr.glade2
gladedir = $(datadir)/pcsxr

desktopdir = $(datadir)/pcsxr
desktop_DATA = pcsxr.desktop

EXTRA_DIST = $(glade_DATA) pcsxr.desktop  
```

I guess before i messed with it, it was 

```
glade_DATA = pcsxr.glade2
gladedir = $(datadir)/pcsxr

desktopdir = $(datadir)/application
desktop_DATA = pcsxr.desktop

EXTRA_DIST = $(glade_DATA) pcsxr.desktop  
```

---

### Post by thatguruguy on 2011-07-21
Why are you trying to compile it?  Just install the deb.  You can get it [here]("http://pcsxr.codeplex.com/releases/view/50048").

---

### Post by thatguruguy on 2011-07-21
Or, just install the playdeb repository (instructions [here]("http://www.playdeb.net/updates/ubuntu/11.04/#how_to_install")) and then you can install the game straight from synaptic or the Ubuntu Software Center.  Or, if you really, really want to use the command line, you can install it by using apt-get install or aptitude.

---

### Post by |{urse on 2011-07-21
nvm, do what he said lol

---

### Post by thatguruguy on 2011-07-21
Also, there is no reason to bump your thread less than an hour after you posted it.

---

### Post by freshmeat20 on 2011-07-21
The .Deb that comes from codeplex doesnt have the opengl drivers with it. When I download it the gui runs as pcsx 1.7 but the help/about says it IS pcsxr 1.9 but still no opengl. I tried putting the opengl driver in the plugins but I get the 'Wrong ELF CLASS' error because i'm running 64bit.... And just for the sake of learning I'm trying to compile lol. What would the apt-get package name be? I tried apt-get install pcsxr but it wasn't there.

Thanks for the quick responses!

---

### Post by thatguruguy on 2011-07-21
Assuming you installed the playdeb repository, it's:
```

sudo apt-get install pcsxr
```

And I'm running Natty 64-bit, and I downloaded the game from the codeplex site, AND I'm using the openGL plugin.  I don't know why you aren't able to use the plugin, unless you've messed something up. 

As far as the splash screen, they've never changed it to reflect that it's 1.9.  If you check on the "about" section under help, it will show that it's pcsx-reloaded 1.9.92.

---

