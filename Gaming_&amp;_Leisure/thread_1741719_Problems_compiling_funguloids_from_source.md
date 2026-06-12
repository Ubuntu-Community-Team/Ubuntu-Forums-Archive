---
title: "Problems compiling funguloids from source"
date: 2011-04-28
forum: Gaming &amp; Leisure
---

### Post by Jonas thomas on 2011-04-28
Ok.. So I really should be focusing on my C++ homework... But my 8 year daughter would really like to play this funguloids...
(What's a dad to do especially after she says... But Dad... you're spending all this time on your C++ class you should be able to make it work... (no pressure.. here...) 

Anyway... Apparently when I download the precompiled version from synaptic, it fires up but as soon as we hit start game it crashes...

No... Problem, I'll build it from source..
[http://funguloids.sourceforge.net/download.html]("http://funguloids.sourceforge.net/download.html")

I managed to all the .dev files off synaptic... and basically got ./configure to run find.

I run make, I'm getting this error.
> jonas@jonas5:~/funguloids$ make
Making all in include
make[1]: Entering directory `/home/jonas/funguloids/include'
make  all-am
make[2]: Entering directory `/home/jonas/funguloids/include'
make[2]: Leaving directory `/home/jonas/funguloids/include'
make[1]: Leaving directory `/home/jonas/funguloids/include'
Making all in src
make[1]: Entering directory `/home/jonas/funguloids/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -I../include/SimpleIni -I/usr/include/lua5.1  -I/usr/include/OIS   -DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/OGRE    -g -O2 -MT funguloids-mpakogre.o -MD -MP -MF ".deps/funguloids-mpakogre.Tpo" -c -o funguloids-mpakogre.o `test -f 'mpakogre.cpp' || echo './'`mpakogre.cpp; \
	then mv -f ".deps/funguloids-mpakogre.Tpo" ".deps/funguloids-mpakogre.Po"; else rm -f ".deps/funguloids-mpakogre.Tpo"; exit 1; fi
In file included from mpakogre.cpp:32:
../include/mpakogre.h: In member function &#8216;virtual Ogre::Archive* MPakArchiveFactory::createInstance(const Ogre::String&)&#8217;:
../include/mpakogre.h:70: error: cannot allocate an object of abstract type &#8216;MPakArchive&#8217;
../include/mpakogre.h:38: note:   because the following virtual functions are pure within &#8216;MPakArchive&#8217;:
/usr/include/OGRE/OgreArchive.h:174: note: 	virtual time_t Ogre::Archive::getModifiedTime(const Ogre::String&)
make[1]: *** [funguloids-mpakogre.o] Error 1
make[1]: Leaving directory `/home/jonas/funguloids/src'
make: *** [all-recursive] Error 1
jonas@jonas5:~/funguloids$ 

There is a set of patches on the site... But I don't understand how to apply them... Nothing in the readme/ install and my normal googling is pulling up anything for me either.  So.. something is telling me I'm missing something embarrassingly obvious.. I suppose I should contact the  developers directly, but I thought I through it out here first?
Anyone... Any ideas??

---

### Post by Perfect Storm on 2011-04-28
It would be easier though to grab the game at playdeb.net and see if it works first.

[http://www.playdeb.net/software/Funguloids](http://www.playdeb.net/software/Funguloids)


EDIT: Moved to gaming section.

---

### Post by Jonas thomas on 2011-04-28
> **Artificial Intelligence said:**
> It would be easier though to grab the game at playdeb.net and see if it works first.

[http://www.playdeb.net/software/Funguloids](http://www.playdeb.net/software/Funguloids)


EDIT: Moved to gaming section.

Nice thought... But I get this error. When I try to install
> 
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch [http://archive.canonical.com/dists/lucid/Release.gpg](http://archive.canonical.com/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Perfect Storm on 2011-04-28
That's not playdeb repository that failed, but Ubuntus. It may be that everybody is upgrading/installing atm. due to new ubuntu release. The servers get heated.

Try later.

---

### Post by Jonas thomas on 2011-04-28
> **Artificial Intelligence said:**
> That's not playdeb repository that failed, but Ubuntus. It may be that everybody is upgrading/installing atm. due to new ubuntu release. The servers get heated.

Try later.

I think I managed to get it downloaded.... I'm getting this message

> Package 'funguloids' is already installed

Is this executable from the games->arcade->funguloids or do I need to do this from the command prompt.
when I execute from the games->arcade->funguloids the program fires up but as soon as I start game it crashes..  I'm reasonably sure that I had uninstalled from the software center that which was loaded from synaptic?

But I didn't get a password request when I downloaded from the site...???

---

### Post by Perfect Storm on 2011-04-28
If you have synaptic/s. center/apt-get used with 15 min it will still "remember" when you typed in the password.


If you are not sure if Funguloids was uninstall, it might be a good idea to try again.

---

### Post by Jonas thomas on 2011-04-28
> **Artificial Intelligence said:**
> If you have synaptic/s. center/apt-get used with 15 min it will still "remember" when you typed in the password.


If you are not sure if Funguloids was uninstall, it might be a good idea to try again.

Ok.. I did a "sudo apt-get remove funguloids" which worked fine.

I downloaded from the link you provided and successfully installed...
Game fired up with sound and as soon as I hit start game it crashed.
(If I could get this game to compile from source... perhaps I could run it in the code::blocks debugger to see what's going on ... :confused:

---

### Post by Perfect Storm on 2011-04-28
okay, I never got it working even compiling. Ogre is tedious to compile correctly.

But here you are. Funguloids needs six patches to OGRE, not to OGRE itself but funguloids.
```
 patch -p0 < ../openalsoundsystem.cpp.diff
  patch -p1 < ../funguloids-gcc44.patch 
  patch -p0 < ../funguloids-ogre_1.6.patch 
  patch -p0 < ../funguloids-strcmp.patch 
  patch -p0 < ../size_chunks_reverse.patch 
  patch -p0 < ../funguloids-lua.patch 
```

Try read the arch package, it will explain more: [https://aur.archlinux.org/packages/funguloids/PKGBUILD](https://aur.archlinux.org/packages/funguloids/PKGBUILD)

---

### Post by Jonas thomas on 2011-04-28
> **Artificial Intelligence said:**
> okay, I never got it working even compiling. Ogre is tedious to compile correctly.

But here you are. Funguloids needs six patches to OGRE, not to OGRE itself but funguloids.
```
 patch -p0 < ../openalsoundsystem.cpp.diff
  patch -p1 < ../funguloids-gcc44.patch 
  patch -p0 < ../funguloids-ogre_1.6.patch 
  patch -p0 < ../funguloids-strcmp.patch 
  patch -p0 < ../size_chunks_reverse.patch 
  patch -p0 < ../funguloids-lua.patch 
```

Try read the arch package, it will explain more: [https://aur.archlinux.org/packages/funguloids/PKGBUILD](https://aur.archlinux.org/packages/funguloids/PKGBUILD)

so... I'm looking at the PKGBUILD file you mentioned... I looks like if I just fire that up... It should basically take care of all the stuff that needs to be fixed... So.. according to this link [http://plugapps.com/index.php5/Developers:_Building_Packages]("http://plugapps.com/index.php5/Developers:_Building_Packages") all I need to do go to the folder that contains the PKBUILD and run makepkg??
But I don't have makepkg and apparently this is something that's not available in synaptic?  Is there another way to run PKBUILD?
Just a silly question... Why hasn't someone just adjusted the code in sourceforge instead of going through all this?

---

### Post by Perfect Storm on 2011-04-28
No, it's Arch Linux "package", it was to give you a hint how the patch OGRE Funguloids.

---

### Post by Jonas thomas on 2011-04-30
> **Artificial Intelligence said:**
> No, it's Arch Linux "package", it was to give you a hint how the patch OGRE Funguloids.

Ok... Got the home projects done... Got a little time before the final... Back to funguloids.. Thanks for the guidance on the patches... 
I went wound up going to the source forge.. got the source and patches and applied them.
./configure, make make install seem to have gone off without a hitch...
When I execute funguloids from the terminal prompt, I get this.

> jonas@jonas5:~$ funguloids
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
FreeImage version: 3.10.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
${datarootdir}/funguloids/plugins.cfg not found, automatic plugin loading disabled.
*-*-* OGRE Initialising
*-*-* Version 1.6.4 (Shoggoth)
An exception has occured: OGRE EXCEPTION(6:FileNotFoundException): '${datarootdir}/funguloids/plugins.cfg' file not found! in ConfigFile::load at OgreConfigFile.cpp (line 84)funguloids: /usr/include/OGRE/OgreSharedPtr.h:152: T* Ogre::SharedPtr<T>::operator->() const [with T = Ogre::Material]: Assertion `pRep' failed.
Aborted
jonas@jonas5:~$ 


It seems I have plugins.cfg
> jonas@jonas5:~$ locate plugins.cfg
/etc/OGRE/plugins.cfg
/etc/OGRE/plugins.cfg.cgprogrammanager
/home/jonas/.local/share/Trash/files/funguloids/bin/plugins.cfg.in
/home/jonas/funguloids/bin/plugins.cfg
/home/jonas/funguloids/bin/plugins.cfg.in
/usr/local/share/funguloids/plugins.cfg
jonas@jonas5:~$ 

I'm a bit confused by the error message plugins.cfg seems to exist but
 OgreConfigFile.cpp doesn't.  

Is the issue with Ogre now? Anythoughts??

---

### Post by Jonas thomas on 2011-05-01
It seems that a bug reported on this.
[https://bugs.launchpad.net/ubuntu/+source/funguloids/+bug/453843]("https://bugs.launchpad.net/ubuntu/+source/funguloids/+bug/453843")

So... I think what's going on is either a bug in Ogre or something in funguloids feeding into this..  I wonder if the next step is to compile the latest and greatest Ogre??  Does anyone have any thought on this?

---

### Post by FuFu Tantrum on 2011-07-15
Did you ever get this settled? If not I may have a solution for you. After a quick google search, I found this [http://funguloids.sourceforge.net/files/funguloids.mpk.zip](http://funguloids.sourceforge.net/files/funguloids.mpk.zip), but I didn't know what to do with it. Basically, I just found the funguloids.mpk file that was installed from synaptic, removed it, and put the .mpk from that download in it's place. I found the original in /usr/share/games/funguloids. Let me know if that works.

---

