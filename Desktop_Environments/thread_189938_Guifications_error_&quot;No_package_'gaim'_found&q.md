---
title: "Guifications error &quot;No package 'gaim' found&quot;"
date: 2006-06-05
forum: Desktop Environments
---

### Post by sbaush on 2006-06-05
Hi all.
I've updated gaim with the .deb on  
```
deb http://people.ubuntu.com/~seb128/deb ./
```
I've downloaded guifications plugin from guifications.sourceforge.net
When i run the configure script i've this error:
```
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

How can i install it?

---

### Post by vaskark on 2006-06-05
[quote=sbaush]Hi all.
I've updated gaim with the .deb on  
```
deb http://people.ubuntu.com/~seb128/deb ./
``` I've downloaded guifications plugin from guifications.sourceforge.net
When i run the configure script i've this error:
```
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
``` 
How can i install it?[/quote] Try installing gaim-dev:

sudo apt-get install gaim-dev

---

### Post by yaztromo on 2006-06-07
I'm trying to install the gaim guifications also now that I have 2 beta 3 installed.

When I try to install gaim-dev

> 
The following packages have unmet dependencies.
  gaim-dev: Depends: gaim (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) but 1:2.0.0-1beta3 is to be installed
            Depends: gaim-data (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) but 1:2.0.0-1beta3 is to be installed
E: Broken packages


Does anyone know what I should do?

---

### Post by msak007 on 2006-06-12
I'd like to the solution to that one. I get the same error when trying to install gaim-dev. Apparently it breaks the current install because that dev package is so old it requires a version <= 1.5 (or 1.5.1 cvs) :confused:. Unfortunately the gaim sourceforge site only has the 2.0 beta dev version in rpms for FC (no source???), so unless you use alien to install it we're stuck and that's a path I don't want to take. I don't remember having problems with Breezy, but that's probably because I installed gaim from source. Looks like I'm back to that route, I'll let you know how it works. *sigh* All this for one plugin (albeit the best one)...

P.S. I don't think that adjusting the PKG_CONFIG_PATH environment variable will help. If I'm not mistaken it's looking for a gaim.pc file. I already checked the pkgconfig folder (/usr/lib/pkgconfig) and there's no sign of a gaim config file. I searched the whole comp for any variation of a gaim.pc file, and couldn't find one so I wouldn't know where to point it. If anybody's got any insight on this or I'm mistaken please let me know.

---

### Post by cskeide on 2006-06-26
I just installed gaim 2.0 beta3 using "--prefix=/opt". In order to install guifications I had to configure it with this command:```
PKG_CONFIG_PATH=/opt/gaim-2.0.0beta3/lib/pkgconfig ./configure --prefix=/opt

```Hope this helps.

---

### Post by yaztromo on 2006-06-26
There was a .deb posted in a thread for guifications on gaim 3 beta 3 that worked for me. I can't find it now so I'll host it when I get home (about 8 hours).

---

### Post by yaztromo on 2006-06-26
[QUOTE=yaztromo]There was a .deb posted in a thread for guifications on gaim 3 beta 3 that worked for me. I can't find it now so I'll host it when I get home (about 8 hours).[/QUOTE]

Here you go: [http://www.tangledwires.co.uk/gaim-guifications_2.13-3_i386.deb]("http://www.tangledwires.co.uk/gaim-guifications_2.13-3_i386.deb")

---

