---
title: "[SOLVED] Some problems installing OGRE"
date: 2008-10-03
forum: Gaming &amp; Leisure
---

### Post by semitone36 on 2008-10-03
Hey all

So I was following the guide to install Vega Strike ([http://gaming.gwos.org/doku.php/guides:64bit:vega_strike](http://gaming.gwos.org/doku.php/guides:64bit:vega_strike)) but i ran into some problems after I ran: 
./configure --with-platform=GLX --prefix=/usr 
 
and I got this:
```
checking for cgCreateProgram in -lCg... no
configure: error:
	****************************************************************
	* You do not have the nVidia Cg libraries installed.           *
	* Go to http://developer.nvidia.com/object/cg_toolkit.html     *
	* (Click on Cg_Linux.tar.gz).                                  *
	* You can disable the building of Cg support by providing      *
	* --disable-cg to this configure script but this is highly     *
	* discouraged as this breaks many of the examples.             *
	****************************************************************
```

So I went to the site and downloaded the Linux x86_64 .tgz file but I dont really know what to do next.

On the guide it says to download and install the CG Program Manager before OGRE but the provided link was dead and I cant seem to find a CG .deb file anywhere else.  I have a feeling that it is because I dont have this installed that I cant complete the installation.  Does anyone know what I can do?

---

### Post by Perfect Storm on 2008-10-04
It's the SVN release (Development release + latest bleeding); If you just want to play get the stable; [http://vegastrike.sourceforge.net/getfiles/](http://vegastrike.sourceforge.net/getfiles/)

```
tar -jvxf vegastrike-linux-0.5.0.tar.bz2
```

EDIT;
I have attached a tar.gz just unpack it and there's a .deb package of CG.

---

### Post by semitone36 on 2008-10-04
> **Artificial Intelligence said:**
>  If you just want to play get the stable


Haha Ill have to remember this next time I want to install a game, This was WAY easier! Thanks AI. 

While Im here would you happen to know how I can use one of the VS logos that came with the stable to make a launcher on my panel?

---

