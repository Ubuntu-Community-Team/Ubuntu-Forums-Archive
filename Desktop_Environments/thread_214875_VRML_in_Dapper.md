---
title: "VRML in Dapper"
date: 2006-07-13
forum: Desktop Environments
---

### Post by jazzgossen on 2006-07-13
I'm trying to install a VRML viewer, without success so far.

I installed openvrml-lookat, but that one seems very limited (or stringent), and won't display any of my VRML files.

Freewrl used to be in the Warty repositories, but I can\t find it in the Dapper ones. I tried installing it from source, but cancelled since I would apparently need to install libosmesa6-dev, which as far as I understand would force me to remove nvidia-glx.

Does anyone else have some ideas of a decent VRML viewer?

---

### Post by DeadEyes on 2006-07-13
Try Cortona it's a browser plugin.
Edit: sorry forget that I think only works in windows

---

### Post by crc_canada on 2006-07-17
We have FreeWRL build guidelines in the FreeWRL FAQ. We do not yet have a package made for Ubuntu.

FreeWRL should run both on the command line, and as a browser plugin (amd64 not verified yet).

If you get the latest source from CVS, it should have the correct files to allow you to run it from the desktop menu system. (this was added this morning)

Here is the link to the ubuntu 6.06 faq entry:

[http://freewrl.sourceforge.net/ubuntu606.html](http://freewrl.sourceforge.net/ubuntu606.html)

and to the faq itself:

[http://freewrl.sourceforge.net/faq.html](http://freewrl.sourceforge.net/faq.html)

and to the FreeWRL home page:

[http://freewrl.sourceforge.net/](http://freewrl.sourceforge.net/)

John Stewart
FreeWRL maintainer.

---

### Post by crc_canada on 2006-07-20
Ok - we have put up a 32 bit package of FreeWRL for Ubuntu 6.06 on freewrl.sourceforge.net

I am currently building an AMD64 box to attempt to build FreeWRL on it.

[http://freewrl.sf.net](http://freewrl.sf.net), on the downloads page, should be an Ubuntu binary (once the mirrors spread it around...)

Comments *more* than welcome; we are building this for the Ubuntu community, hopefully it is a product that is packaged well, and that the community wants.

Please feel free to email me comments/criticism/praise/whatever.

John Stewart
CRC Canada.

---

### Post by Defscanguci on 2006-12-12
I'm stuck at the [COLOR="Red"]sudo make[/COLOR] stage. I get this error:

...
make[1]: Leaving directory `/home/brian/Desktop/freewrl-1.18.9/JS/js1.5/src'
gcc -c -O2 -g -pipe -fno-strict-aliasing -fPIC -I/usr/X11R6/include/ -I/usr/include/freetype2 -I/usr/include/freetype2/freetype -IJS/js1.5/src/Linux_All_OPT.OBJ -IJS/js1.5/src -ICFuncs -ICFrontEnd  -IPlugin/netscape/include -ansi -DHAVE_MOTIF -DXP_UNIX -D_GNU_SOURCE    -c -o CFuncs/Component_Networking.o CFuncs/Component_Networking.c
CFuncs/Component_Networking.c: In function ‘compile_ReWireMidiControl’:
CFuncs/Component_Networking.c:81: error: invalid lvalue in assignment
CFuncs/Component_Networking.c: In function ‘do_ReWireMidiControl’:
CFuncs/Component_Networking.c:122: warning: passing argument 1 of ‘compileNode’ from incompatible pointer type
make: *** [CFuncs/Component_Networking.o] Error 1


I can't seem to find much elsewhere about this error, just what can cause it in general. Teh ideas?

---

### Post by jazzgossen on 2006-12-13
Try the Ubuntu deb file at freewrl.sourceforge.com. I just installed it without problems. Well, it only handles VRML 2.0, and most of my files are in VRML 1.0 format, but at least the installation went flawlessly.

---

### Post by KittyChunk on 2007-07-19
Hi John, thanks very much for your efforts at putting together install packages for Ubuntu. FreeWRL is one of the only X3D viewers available in this form, which makes deployment extremely simple.

Just a comment that you may want to think about supporting packages for 6.06 (Dapper) into the future, as it was a Long-Term Support release from the developers (3 years' support on the desktop if memory serves?). We have the situation that our cluster is still running 6.06, even though my laptop and the other desktop machines are on 7.04. I had some difficulty compiling FreeWRL from source on the 6.06 machines, so at the moment I'm viewing all my X3D visualisations over the network from my laptop - not ideal :)

I searched for the 6.06 packages mentioned above on Sourceforge, but I couldn't find them in any of the obvious places - looks like they may have been superceded by the 6.10 and 7.04 debs.

---

