---
title: "Need help with custom Usplash creation"
date: 2009-04-09
forum: Desktop Environments
---

### Post by Ampersand. on 2009-04-09
first of all i hope this is in the right section.

Im on Hardy by the way.
I have been trying to make my own usplash for a while and im having some problems with making the .so file and some colour reducing things too.
 
i found a few how-to's and followed them as closely as i could but first of all:
i seem to have some problems with setting the colours to 256. no matter what dithering setting i choose the text gets pixelated and just doesnt look good. see the attached files if you are interested. (Text Problem is before, Text Problem 2 is after)
what is strange is that the colours that are used in the anti-aliasing are used elsewhere in the image. short of drawing the text after instead of using text in gimp im not sure what to do.

second is the compiling(?) i might have a problem with running the scripts. If i do:

$ user=$user ; cd /home/user/Documents/Themes/BootTheme/ && dpkg-buildpackage -rfakeroot

or any variations of that i get this printout:

dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1

and dont get a .so file.

EDIT: well i fixed that error by downloading the source for xubuntu and modifying that instead, there seems to be no difference between that changelog and the one i was using but now it runs though the script. I might add that it goes to some 60000 lines with a warning about some kind of large truncated integer string.
However i still end up without a .so file for no reason i can fathom.

so any advice would be greatly appreciated. I dont think i could show you the whole splash screen because i have stolen the background from someone i dont think would appreciate it being publicly shown.
thanks guys

Im going to keep looking for answers and i will post the results here but it is going to take a while.

---

### Post by Ampersand. on 2009-04-24
Some developments:
Embrace (who made the fingerprint, Afisufi and Comptus Boot splashes along with a bunch of other stuff) let me know that you dont need some complicated command to compile the .so file. 
Here is what you do and what worked for me.

do cd /home/user/Themes (or wherever else you have the theme stuff)
then just type make

you are done.

Now i just need to do some fine tuning to make it look more pretty:
-The colours seem to be a little strange at the moment, ill need to fool around in GIMP to see what happens.
-The progress bar is inside a black square but i just want it to be floating inside a transparent area so the background shows through. It is also in the wrong place at the moment. easily fixed i think.
-I want to figure out how to make the progress bar load from bottom to top rather than left to right. Not even sure if it is possible but if it works then hooray.

This is a work in progress so i will post the results here, if anyone cares.

---

