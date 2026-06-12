---
title: "Wine 0.9.24 Compiling =&gt; Segmentation fault: Possible solution"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by spacyspacy on 2006-10-29
Wine worked for me when compiling with the following configure call:

```
./configure -fno-stack-protector
```

Hope this can help some people :cool:

---

### Post by Protoss on 2006-10-29
I get 
```
configure: error: unrecognized option: -fno-stack-protector

```, is there something else? I am using Edgy.

---

### Post by AshyRaccoon on 2006-10-29
Edit:
I tried this:
sudo make uninstall
export CFLAGS=-fno-stack-protector
./configure
make depend
make
sudo make install
wine

That worked.  I can now run winecfg and wine without segfaults.
A post in [https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965](https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965) says -fno-stack-protector goes in CFLAGS.

---

### Post by Protoss on 2006-10-29
This fixes the seg-faults but I can no longer run WoW in OpenGL, I am forced to run it in D3D mode.

---

### Post by ajackson on 2006-11-02
If you add -O2 to your CFLAGS you can get WoW working with wine 0.9.24, this has been fixed and should be ok come 0.9.25

---

### Post by reiki on 2006-11-02
No longer a need to compile for Edgy if you don't want to.
If you've already compiled it (and it's not working for you) you can go back to your source directory (where you installed it from) and sudo make uninstall. Then just make sure you have the winehq repositories:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

just apt-get install wine

Then go to [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) and just grab the patched binary. One file. On edgy, your original will be /usr/lib/wine/winex11.drv.so . Rename the original and copy in the replacement. It's patched for the infamous nVidia flicker as well. 

If you want to compile and you get the error:
configure: error: unrecognized option: -fno-stack-protector
that means your gcc version is 4.0 or less. In that case, you don't need to set that CFAG. Just leave that part out. If you apt-get install build-essentials on Edgy you get gcc-4.1. It was in the 4.1 version that the CFLAG="-fno-stack-protector" became necessary. HOWEVER some folks still had issues and what was discovered was that an additional flag parameter was needed.
CFLAG="-fno-stack-protector -O2" (that's a letter O, not a number). 

You can get this working without having to compile it yourself and by letting apt build a .deb package for you. I have another post on here about WoW, Wine, and Edgy that explains this and it's not difficult and was actually in the help.ubuntu.org site for Breezy and Dappy and still works for Edgy by changing appropriate repos and filenames. And in fact, running apt-buildpackage is where the additional CFLAG parameter was observed.

And I'm not smart enough to know all this on my own. Many thanks and much credit is due to Nick Law and AlanJ over at appdb.winehq.org. for getting this straightened out. I just helped test. --- Charlie

---

