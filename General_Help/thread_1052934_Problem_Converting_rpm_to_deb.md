---
title: "Problem: Converting rpm to deb"
date: 2009-01-28
forum: General Help
---

### Post by Phoenix777 on 2009-01-28
I have three rpm files that I need to convert to deb files:

Maya2009_0_64-docs_en_US-2009.0-63.x86_64.rpm
AWCommon-server-11.5-19.i686.rpm 
AWCommon-11.5-19.i686.rpm 

So I type the command sudo alien -cv *.rpm

this produces 1 deb file:

maya2009-0-64_2009.0-102_amd64.deb

which is all good, BUT it creates 2 directories that are not deb files:

AWCommon-server-11.5 
AWCommon-11.5 

 on creating these there is an error in terminal:


dpkg-shlibdeps: failure: couldn't find library libXm.so.2 needed by debian/awcommon/usr/aw/COM/bin/installKey (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
	find AWCommon-11.5 -type d -exec chmod 755 {} ;
find: `AWCommon-11.5': No such file or directory
	rm -rf AWCommon-11.5

So how do I either fix these errors or go about creating deb files from these directories.

---

### Post by HermanAB on 2009-01-28
Find the project home page, get the source code and recompile it.  Trying to convert packages usually doesn't work.

Cheers,

Herman

---

### Post by jespdj on 2009-01-28
> dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
Also, it seems that you are trying to convert a package for 32-bit Linux to a package for 64-bit. That's probably not supported.

---

### Post by Phoenix777 on 2009-01-28
I am running 64 bit Hardy and the program that I want to convert is for 64 bit linux, although it is not distributed for ubuntu.

I managed to do this 3 months ago, but I can't remember how I did it. My harddrive died so now I have to start again.

---

