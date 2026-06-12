---
title: "Zsnes 1.42 SDL error"
date: 2005-12-07
forum: Gaming &amp; Leisure
---

### Post by Strag0 on 2005-12-07
I've had one mind numbing error when trying to run Zsnes 1.42. Every time I try to execute the program I get a SDL error. "Fatal signal: Segmentation Fault (SDL Parachute Deployed)" I've installed All SDL Libs That I think I needed and I still get these. I'd try the WIP version of Zsnes but I can't get the Source to compile correctly. 

Does anyone know a fix for this SDL error?

Thank you!

---

### Post by BoyOfDestiny on 2005-12-08
[QUOTE=Strag0]I've had one mind numbing error when trying to run Zsnes 1.42. Every time I try to execute the program I get a SDL error. "Fatal signal: Segmentation Fault (SDL Parachute Deployed)" I've installed All SDL Libs That I think I needed and I still get these. I'd try the WIP version of Zsnes but I can't get the Source to compile correctly. 

Does anyone know a fix for this SDL error?

Thank you![/QUOTE]

Maybe one is still missing? Try the package libsdl-debian-all (or something like that)

Or, if you like, I have a deb I made from the zsnes cvs a couple of months ago:
[http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb](http://www.safaribans.com/gpl/zsnes-cvs_cvs-20050927-1_i386.deb)

---

### Post by Strag0 on 2005-12-08
Thanks! Your CVS .deb worked perfectly.

Now to see if It'll hold up to some game playing.

---

### Post by BoyOfDestiny on 2005-12-08
[QUOTE=Strag0]Thanks! Your CVS .deb worked perfectly.

Now to see if It'll hold up to some game playing.[/QUOTE]

No problem. If there are any show stoppers, you can try this simple script I made to grab the cvs and build it (or try to build it ;) ):

######
#bash

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/zsnes login
 
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/zsnes co -P zsnes
cd zsnes/src

./autogen.sh

make


#########

Off the top of my head you need : sdl-dev, nasm, autogen, autoconf, build-essential, libpng-dev, zlib-dev, cvs, (and if you want to make your own debs: checkinstall).

Anyway, I notice the forms turns d and : into that smiley... but if you copy it into clipboard should be normal.

---

