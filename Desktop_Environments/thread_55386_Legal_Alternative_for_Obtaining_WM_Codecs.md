---
title: "Legal Alternative for Obtaining WM Codecs?"
date: 2005-08-08
forum: Desktop Environments
---

### Post by SSTwinrova on 2005-08-08
Everyone who has tried to install the Windows codec package knows about its legality issues and that's why Ubuntu can't officially support it (and it must remain in the unofficial extras repo). I haven't read the license agreements so this could be just as much in violation as the deb file is, but could Ubuntu provide some sort of script/program that a user could execute post-installation to download and install the codec package from MS's website? (Direct link: [http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx)](http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx)). Their servers are extremely slow at the time I'm writing this (2 KB/sec for me), but it looks like it's just an EXE that extracts the codecs to the proper directories, and I'm sure someone with scripting/programming experience could figure out how to make use of this to install the codecs in Ubuntu. If this is in violation of the license agreements, the extras repo is still going to be the easiest way; just a thought for increasing compatibility, though.

---

### Post by Takis on 2005-08-09
Knowing MS, they'd probably consider porting their codecs like that to be 'reverse engineering' and against the EULA.

---

### Post by az on 2005-08-09
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg)
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-plugins](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-plugins)

---

### Post by tseliot on 2005-08-10
Have you tried my HOWTO? It works both with Ubuntu 32bit and 64bit.

[http://www.ubuntuforums.org/showthread.php?t=54399](http://www.ubuntuforums.org/showthread.php?t=54399) 

I hope you like it

---

### Post by SSTwinrova on 2005-08-10
tseliot: Your HOWTO would be useful for people without internet access (or if they feel wrong downloading the package), but I don't fall into either of those categories.   ;-) -- My suggestion was more along the lines of allowing Ubuntu to be able to link to the MS Download site and have a script that would extract the codecs without violating any licenses from repackaging them.

azz: Why did you link to those to packages? I don't see any references to WMA/V in them...  :?

---

### Post by az on 2005-08-10
As far as I know, ffmpeg can handle wma and mwv.  Can someone confirm this?

---

